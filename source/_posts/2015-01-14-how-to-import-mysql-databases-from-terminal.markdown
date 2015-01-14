---
layout: post
title: "How to import MySQL databases from terminal"
date: 2015-01-14 11:26:49 +0700
comments: true
categories: [CSS3, Sass, Media Queries]
---
The best way to import an existed database to an ubuntu machine is:
*Open terminal (`Ctrl + Alt + T`)
*Open mysql (`$mysql or $mysql -u username -p password`)
*Create your own database(ex: mydatabase)
*Exit mysql(by typing `exit` or `\q`)
*`$mysql -u username -ppassword mydatabase < exitedfile.sql`
###Table names problems in MySQL
When the ProcessMaker workspaces from Windows are restored into Linux, the table names of the workspace databases will be in lowercase. ProcessMaker will not be able to read these tables correctly because it expects the table names to be in uppercase. To work around this problem, either configure MySQL tables to be case insensitive or change the name of the tables of the backup to upper-case with a text editor.
####**Configuring MySQL Tables to be Case Insensitive**
Go the Linux/UNIX server and edit the MySQL configuration file, which is generally found at `/etc/mysql/my.cnf, /etc/my.cnf or ~/my.cnf`
Add the following line to the my.cnf configuration file:
`lower_case_table_names=1`
Then restart MySQL (or reboot):
**Debian/Ubuntu/SuSE**
`/etc/init.d/mysql restart`
**Red Hat/CentOS/Fedora:**
`/etc/init.d/mysqld restart`
####Restoring ProcessMaker Database on Linux
Run the following command to restore Databases:
`mysql -u root - < name_backup.sql`
####Changing the rp_workflow database name
Change the rp_workflow database name by executing the following command:
`mysqldump -u *user -password* rpworkflow | mysql -u *user* -'password *rp_workflow*`
Finally run the processmaker upgrade command:
`php-f processmaker upgrade`