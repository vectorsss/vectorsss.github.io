---
title: "Sublime Text3下两款Markdown插件 支持实时预览与代码高亮"
date: "2017-05-04"
categories: 
  - "工具-效率"
tags: 
  - "工具-效率"
url: "/archives/105"
---

# Sublime Text3 安装 Package Control

快捷键 `ctrl`+`` ` ``

- Sublime Text3安装Package Control代码如下
    
    > import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed\_packages\_path(); urllib.request.install\_opener( urllib.request.build\_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( '[http://packagecontrol.io/](http://packagecontrol.io/)' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    
- Sublime Text2安装代码
    
    > import urllib2,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed\_packages\_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install\_opener( urllib2.build\_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( '[http://packagecontrol.io/](http://packagecontrol.io/)' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
    

[如果代码失效，点击进入官网查看最新代码](https://packagecontrol.io/installation#st3)

# 安装OmniMarkupPreviewer+Markdown Preview

`Ctrl`+`shift`+`p`

1. install package
2. 找到OmniMarkupPreviewer安装,完成之后可以使用`ctrl`+`alt`+`o`在浏览器中预览。
3. 与上一步相同找到Markdown Preview并安装。
4. [OmniMarkupPreviewer默认配置一般足够使用，详细配置点击进入](http://macplay.leanote.com/post/%E8%BF%91%E4%B9%8E%E5%AE%8C%E7%BE%8E%E7%9A%84-Markdown-%E5%86%99%E4%BD%9C%E4%BD%93%E9%AA%8C-Sublime-Text-3-OmniMarkupPreviewer)
5. 设置语法高亮和mathjax支持。
    
    `Preference -> Package Setting -> Markdown Preview -> Setting - Default`
    
    Ctrl+a 全选 复制到 `Setting - User`(也可以直接在Default里面保存，如果提示找不到路径，自己创建一个即可)
    
    找到`"enable_mathjax": false,` `"enable_highlight": false,` 将false改为true即可。
6. 找一款适合自己的主题，我用的Material Theme。
