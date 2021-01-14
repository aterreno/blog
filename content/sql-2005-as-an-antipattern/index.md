---
title: "SQL 2005 as an antipattern"
description: ""
date: "2007-02-28T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/sql-2005-as-an-antipattern-74ffcb85506c
redirect_from:
  - /sql-2005-as-an-antipattern-74ffcb85506c
---

After 1 month and an half working on the strange combination of EJBs and SQL 2005 I can say that not only EJBs are an antipattern but also the bloody SQL server of Microsoft.

We had so many troubles doing an automated backup and restore of a database, the last one was a permission problem that you can fix using a stored procedure (oh my God I wrote that I am using a stored procedure from Microsoft running onÂ Microsoft RDBMS!) that it’s shipped with that kind of RDBMS. Is very nice the code, Action=Auto\_Fix.

How much easier and safer is to backup a MySql server(\*)?

This problem was just the last one, and I need to yell out a bit.

> [STG Forums :: View topic — SQL login problems after a backup/restore](http://forums.seattletech.com/viewtopic.php?p=333&sid=9bf0a2797b1ff982fde06a985e78d1fe)  
> To fix this problem, run the following SQL commands:  
> Code:  
> Exec sp\_change\_users\_login @Action = ‘Auto\_Fix’, @UserNamePattern = ‘tsmith’

That’s what happens with some folks without knowledge of what are good programming practices write a RDMS. I just wanna paste here the code (part of) of the Stored Procedure. It’s SQLserver two thousand five and someone still write shit code like this:

> — ERROR IF NOT AUTO\_FIX —   
> if @Action ‘AUTO\_FIX’  
> begin  
> raiserror(15286,-1,-1,@ActionIn)  
> return (1)  
> end

> — HANDLE AUTO\_FIX —   
>  — CHECK PERMISSIONS —   
> if not is\_srvrolemember(‘sysadmin’) = 1  
> begin  
> dbcc auditevent (130, 14, 0, NULL, @UserNamePattern, NULL, NULL, NULL, NULL, NULL)  
> raiserror(15247,-1,-1)  
> return (1)  
> end  
> else  
> begin  
> dbcc auditevent (130, 14, 1, NULL, @UserNamePattern, NULL, NULL, NULL, NULL, NULL)  
> end

> — VALIDATE PARAMS —   
> if @UserNamePattern IS Null or @LoginName IS NOT Null  
> begin  
> raiserror(15600,-1,-1,’sys.sp\_change\_users\_login’)  
> return (1)  
> end

> — LOOP THRU ORPHANED USERS —   
> select @exec\_stmt = ‘declare ms\_crs\_110\_Users cursor global for  
> select name from sysusers  
> where name = N’ + quotename( @UserNamePattern , ‘’’’)+ ‘  
> andÂ Â issqluser = 1  
> andÂ Â sid is not NULL  
> andÂ Â len(sid) 0 or suser\_sid(@110name) is null  
> begin  
> raiserror(15497,16,1,@110name)  
> deallocate ms\_crs\_110\_Users  
> return (1)  
> end  
> select @FixMode = ‘1AddL’  
> raiserror(15293,-1,-1,@110name)  
> end  
> else  
> begin  
>  — REPORT ERROR & CONTINUE IF DUPLICATE SID IN DB —   
> select @FixMode = ‘2UpdU’  
> raiserror(15292,-1,-1,@110name)  
> end

> select @loginsid = suser\_sid(@110name)  
> if not exists (select \* from sysusers where sid = @loginsid)  
> begin  
>  — LOCK USER —   
> BEGIN TRANSACTION  
> EXEC %%Owner(Name = @110name).Lock(Exclusive = 1)  
>  — UPDATE SYSUSERS ROW —   
> if @@error = 0  
> begin  
> EXEC %%UserOrGroup(Name = @110name).SetSID(SID = @loginsid,  
> IsExternal = 0, IsGroup = 0) — may fail  
> if @@error 0  
> begin  
> ROLLBACK TRANSACTION  
> deallocate ms\_crs\_110\_Users  
> raiserror(15063,-1,-1)  
> return (1)  
> end  
> end  
> COMMIT TRANSACTION

> if @FixMode = ‘1AddL’  
> select @cfixesaddlogin = @cfixesaddlogin + 1  
> else  
> select @cfixesupdate = @cfixesupdate + 1  
> end  
> else  
> raiserror(15331,-1,-1,@110name)

> fetch next from ms\_crs\_110\_Users into @110name  
> end — loop  
> close ms\_crs\_110\_Users  
> deallocate ms\_crs\_110\_Users

> — REPORT AND RETURN SUCCESS —   
> raiserror(15295,-1,-1,@cfixesupdate)  
> raiserror(15294,-1,-1,@cfixesaddlogin)  
> return (0) — sp\_change\_users\_login

(\*) Go [here](http://dev.mysql.com/doc/refman/5.0/en/backup.html) if you don’t confide in me, I did that many times, with cron, from ant, never had ANY problems.
