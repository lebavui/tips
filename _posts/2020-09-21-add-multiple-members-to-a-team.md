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
Mở PowerShell ở chế độ Administrator và cài đặt module MicrosoftTeams:
~~~
Install-Module -Name MicrosoftTeams
~~~

Bước 2.
Kết nối với phần mềm Microsoft Teams, ở bước này bạn cần truy nhập vào tài khoản được sử dụng với Teams.
~~~
Connect-MicrosoftTeams
~~~

Bước 3.
Lấy ID của lớp cần thêm sinh viên, giả sử lớp đã được tạo trước đó trong Teams.
~~~
Get-Team -DisplayName "tên_hiển_thị_của_lớp"
~~~

Khi hiển thị kết quả, hãy lưu lại giá trị GroupId.

Bước 4.
Trước khi thực hiện bước này, bạn cần chuẩn bị 1 file văn bản chứa email của sinh viên, mỗi email trên một dòng, với dòng đầu tiên là tên của danh sách. Bạn có thể đặt tên bất kỳ, tên này được sử dụng trong lệnh sau.
Ví dụ về file chứa danh sách email của sinh viên như sau:
~~~
123456
email1
email2
~~~
Để cho thuận tiện thì nên sử dụng mã lớp để làm tên của danh sách (để ở đầu file) và đồng thời là tên của file văn bản.

Sau khi có danh sách nhập lệnh sau để thêm sinh viên vào lớp:
~~~
Import-Csv -Path <tên_file_văn_bản> | foreach{Add-TeamUser -GroupId <mã_id_lớp> -user $_.<tên_danh_sách>}
~~~
Ví dụ:
~~~
Import-Csv -Path 123456.txt | foreach{Add-TeamUser -GroupId feeb99cc-680d-4b32-9c53-3e7b231b4c86 -user $_.123456}
~~~

Chúc các bạn thành công!

Tham khảo: [Medium](https://medium.com/kernelbinary/how-to-add-multiple-members-into-a-team-in-microsoft-teams-using-powershell-8e7021645d8c)
