---
title: "GitLab+Hexo更改数学公式渲染引擎为Pandoc"
date: "2019-03-05"
categories: 
  - "other"
url: "/archives/534"
---

```git
git push origin master
```

当我把远程仓库更新完成的时候, 过了好久发现博客并没有变化. 于是去看了一下Pipelines中的执行过程, 果然报错.

### 问题1: Error: spawn pandoc ENOENT

```
$ hexo deploy
INFO  Start processing
events.js:183
      throw er; // Unhandled 'error' event
      ^

Error: spawn pandoc ENOENT
    at _errnoException (util.js:992:11)
    at Process.ChildProcess._handle.onexit (internal/child_process.js:190:19)
    at onErrorNT (internal/child_process.js:372:16)
    at _combinedTickCallback (internal/process/next_tick.js:138:11)
    at process._tickCallback (internal/process/next_tick.js:180:9)
ERROR: Job failed: exit code 1
```

这个问题的原因是, 由于需要让Hexo支持数学公式渲染, 所以我在本地使用hexo-renderer-pandoc替换了hexo默认的markdown渲染引擎. 而在.gitlab-ci.yml中没有添加且我本地安装了pandoc, 而gitlab-ci里面没有安装. 以下是我的.gitlab-ci.yml配置,第一个是之前的配置, 第二个是修改之后的配置. **配置1**

```yml
image: node:10.15.0
pages:
  cache:
    paths:
    - node_modules/

  script:
  - npm install hexo-cli -g
  - npm install
  - hexo deploy
  artifacts:
    paths:
    - public
  only:
  - master
```

**配置2**

```yml
before_script:
    - apt-get update -qq&&apt-get install -y -qq pandoc
image: node:10.15.0
pages:
  cache:
    paths:
    - node_modules/

  script:
  - npm install hexo-cli -g
  - npm install
  - npm uninstall hexo-renderer-marked --save
  - npm install hexo-renderer-pandoc --save
  - hexo deploy
  artifacts:
    paths:
    - public
  only:
  - master
```

经过这样修改之后,出现了第二个问题.

### 问题2: pandoc exited with code 9: pandoc: Unknown extension: smart

```
$ hexo deploy
INFO  Start processing
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: pandoc exited with code 9: pandoc: Unknown extension: smart

    at ChildProcess.<anonymous> (/builds/Chizhao/chizhao.gitlab.io/node_modules/hexo-renderer-pandoc/index.js:94:20)
    at emitTwo (events.js:126:13)
    at ChildProcess.emit (events.js:214:7)
    at maybeClose (internal/child_process.js:925:16)
    at Socket.stream.socket.on (internal/child_process.js:346:11)
    at emitOne (events.js:116:13)
    at Socket.emit (events.js:211:7)
    at Pipe._handle.close [as _onclose] (net.js:557:12)
ERROR: Job failed: exit code 1
```

出现这个问题的原因是, pandoc从2.0版本之后, 取消了smart这个扩展, 说白了也就是gitlab-ci中安装的pandoc版本太低. 于是我们只要更换一个2.0版本以上的pandoc即可解决.

对应的.gitlab-ci.yml配置如下:

```yml
before_script:
  - wget https://github.com/jgm/pandoc/releases/download/2.7/pandoc-2.7-1-amd64.deb
  - dpkg -i ./pandoc-2.7-1-amd64.deb
image: node:10.15.0
pages:
  cache:
    paths:
    - node_modules/

  script:
  - npm install hexo-cli -g
  - npm install
  - npm uninstall hexo-renderer-marked --save
  - npm install hexo-renderer-pandoc --save
  - hexo deploy
  artifacts:
    paths:
    - public
  only:
  - master
```
