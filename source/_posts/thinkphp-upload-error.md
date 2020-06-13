---
title: 使用 thinkphp 上传文件失败的原因
date: 2016-12-27 13:55:37
categories: 心得
tags:
 - thinkphp
---

之前在使用 thinkphp 时, 使用了其内置的上传文件功能, 在本地时使用正常, 但是放在生产环境中前端会提示上传失败, 原因也不明, 上传目录的权限也够, 就是不知道为什么.

最近使用最新版的 thinkphp5 时又遇到了这个问题, 所以在这里写一篇文章, 让更多的初学者少走弯路, 知道问题所在.

无论是在 thinkphp 还是其他 php 框架下, 上传文件都需要现将文件暂存在 php 的临时目录中, 然后使用 ` move_uploaded_file($_FILES["file"]["tmp_name"])` 方法将临时目录中的文件保存在上传目录.

在知道了这个后, 我们应该__检查一下应用上传目录和 php_temp 目录的权限是否为 777__, 在 IIS 下需要给予足够的权限.

如果你不知道 php_temp 临时目录在哪里也没有设置过, 用 `phpinfo()` 函数查看一下即可.