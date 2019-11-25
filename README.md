![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 一个改变所有数据库所有者的旧技巧
#### Old Trick To Change All Database Owners
**发布-日期: 2016年2月17日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
以下sql逻辑（logic）将简单地将所有数据库所有者更改为“sa”。 这是一种经过验证的方法。影响除系统数据库之外的所有数据库。另外，最终脚本将确认所有数据库所有者已更改为“sa”。 任何人都可以做到这一点，但想发帖帮你节省几个步骤。


## English
The following sql logic will simply change all database owners to ‘sa’. It’s a tried and true method. Will affect all databases excluding the system databases.  Additionally; the final script will confirm all database owners have been changed to ‘sa’.  Anyone can do this, but thought I would post anyway to save you a few keystrokes.

---
## Logic
```SQL
declare @change_db_owners  varchar(max) set @change_db_owners  = ''
select  @change_db_owners   = @change_db_owners +
'exec [' + name + ']..sp_changedbowner ''sa'';' + char(10)
from    sys.databases where database_id > 4
exec    (@change_db_owners) --for xml path(''), type
 
select
'database' = upper(name)
,   'owner' = suser_sname(owner_sid)
from
sys.databases
where
database_id > 4
order by
name asc


```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

