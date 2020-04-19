title: Create ZIP files with ODS PACKAGE statements in SAS 9.2
author: Jun Hu
tags:
  - SAS
date: 2019-02-08 00:50:00
---
Starting in SAS 9.2, you can create your own ZIP files using ODS PACKAGE statements...

<!-- more -->

```
/************ODS begins************/
ods package(dmzip) open nopf;
ods package(dmzip) add file='/folders/myfolders/dm.sas7bdat';
ods package(dmzip) add file='/folders/myfolders/dm2.sas7bdat' path='data/';
ods package(dmzip) publish archive
  properties(
		archive_name='dm.zip' 
		archive_path='/folders/myfolders/'
  );
ods package(dmzip) close;
/************ODS ends************/
```
----------


---


Reference:


*- [SAS Support: Base SAS ODS PACKAGE Resources](http://support.sas.com/rnd/base/ods/odspackages/index.html)*
*- [US CFR 21 Part 11 as of June 6, 2019](https://www.ecfr.gov/cgi-bin/text-idx?SID=8f1ef8a41ee0b4b16030eaeee93dc697&mc=true&node=pt21.1.11&rgn=div5)*
*- [Wikipedia: Trial master file](https://en.wikipedia.org/wiki/Trial_master_file)*
