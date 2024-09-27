---
layout: post
title: Cách reset mật khẩu tài khoản WSL
#subtitle: 
gh-repo: lebavui/tips
tags: [tips, wsl]
comments: false
---

Bước 1.
Mở PowerShell và login vào WSL:
~~~
wsl --user root
~~~

Bước 2a.
Nếu muốn thay đổi mật khẩu tài khoản root.
~~~
passwd
~~~

Bước 2b.
Nếu muốn thay đổi tài khoản khác.
~~~
passwd username
~~~