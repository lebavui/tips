---
layout: post
title: Cách chuyển các file đang làm sang máy khác
#subtitle: 
gh-repo: lebavui/tips
tags: [tips, github]
comments: false
---

Bước 1.
Lưu trữ thay đổi bằng lệnh stash.
~~~
git stash --include-untracked
~~~

Bước 2.
Lưu stash vào file, chú ý lấy đúng stash bằng chỉ có. Có thể dùng lệnh stash list để xem danh sách các stash đã lưu.
~~~
git stash show "stash@{0}" -p > changes.patch
~~~

Bước 3.
Chuyển file patch sang máy tính còn lại.
~~~
git apply changes.patch
~~~