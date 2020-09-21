---
layout: post
title: Cách sử dụng Windows Powershell để thêm nhiều thành viên vào lớp học cùng một lúc
#subtitle: 
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [tips, microsoft teams
]
comments: false
---

Bình thường khi muốn thêm các thành viên vào trong một lớp, ta cần phải thêm từng thành viên một. Đối với lớp học có số lượng sinh viên nhiều, việc này sẽ mất nhiều thời gian.

Bước 1.

~~~
Install-Module -Name MicrosoftTeams
~~~

Bước 2.

~~~
Connect-MicrosoftTeams
~~~

Bước 3.

~~~
Get-Team -DisplayName "tên_hiển_thị_của_nhóm"
~~~

Bước 4.

~~~
Import-Csv -Path <your_csv_file_name_goes_here> | foreach{Add-TeamUser -GroupId YOUR_TEAM_ID -user $_.upn_list}
~~~

Chúc các bạn thành công!

Tham khảo: [Medium](https://medium.com/kernelbinary/how-to-add-multiple-members-into-a-team-in-microsoft-teams-using-powershell-8e7021645d8c)