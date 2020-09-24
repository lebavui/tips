---
layout: post
title: Sử dụng Powershell để thêm nhiều thành viên vào lớp học cùng một lúc
#subtitle: 
gh-repo: lebavui/tips
gh-badge: [star, fork, follow]
tags: [tips, microsoft teams]
comments: false
---

Khi sử dụng Teams, bạn chỉ có thể thêm từng sinh viên vào lớp học. Đối với lớp học có nhiều sinh viên, việc này sẽ mất nhiều thời gian.
Với việc sử dụng PowerShell bạn có thể thêm nhiều sinh viên trong cùng một lúc bằng một vài lệnh đơn giản.

Bước 1.
Mở PowerShell và cài đặt module MicrosoftTeams:
~~~
Install-Module -Name MicrosoftTeams
~~~

Bước 2.
Kết nối với phần mềm Microsoft Teams, ở bước này bạn cần truy nhập vào tài khoản được sử dụng với Teams
~~~
Connect-MicrosoftTeams
~~~

Bước 3.
Lấy ID của lớp cần thêm sinh viên, giả sử lớp đã được tạo trước đó.
~~~
Get-Team -DisplayName "tên_hiển_thị_của_lớp"
~~~

Bước 4.
Trước khi thực hiện bước này, bạn cần chuẩn bị 1 file văn bản chứa email của sinh viên, mỗi email trên một dòng, với dòng đầu tiên là tên của danh sách. Bạn có thể đặt tên bất kỳ, tên này được sử dụng trong lệnh sau.
~~~
Import-Csv -Path <tên_file_văn_bản> | foreach{Add-TeamUser -GroupId YOUR_TEAM_ID -user $_.upn_list}
~~~

Chúc các bạn thành công!

Tham khảo: [Medium](https://medium.com/kernelbinary/how-to-add-multiple-members-into-a-team-in-microsoft-teams-using-powershell-8e7021645d8c)