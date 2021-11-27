

编译测试记录：
(1) D:\Git\bareos_study
(2) D:\Git\JohnnyRead\bareos_test
(3) 文档相关：D:\Project\plugin_fd\bareos


### 关于bareos-fd,bareos-sd,bareos-dir命令行启动时， 相关参数的说明：
https://docs.bareos.org/Appendix/BareosPrograms.html?highlight=bconsole

```shell
# 启动bareos-fd, 并且设置debug level为1000
/usr/local/lib/bareos/scripts/bareos-ctl-fd start "-d 1000" > /tmp/bareos-fd.log 2>&1
# 停止bareos-fd
/usr/local/lib/bareos/scripts/bareos-ctl-fd stop

# 启动bareos-sd, 并且设置debug level为500
/usr/local/lib/bareos/scripts/bareos-ctl-sd start "-d 500" > /tmp/bareos-sd.log 2>&1
# 停止bareos-sd
/usr/local/lib/bareos/scripts/bareos-ctl-sd stop

```




### 概念理解：
Another way of looking at it is the FileSet is what to backup; 
the Client is who to backup; the Schedule defines when, 
and the Pool defines where (i.e. what Volume).

### 任务测试

```shell
## FileSet中配置
root@johnny_server:/usr/local/etc/bareos/bareos-dir.d/fileset# cat SelfTest.conf 
FileSet {
  Name = "SelfTest"
  Description = "fileset just to backup some files for selftest"
  Include {
    Options {
      Signature = MD5 # calculate md5 checksum per file
    }
    File = "/usr/local/sbin/bconsole"
  }
}

## job中配置
root@johnny_server:/usr/local/etc/bareos/bareos-dir.d/job# cat backup-bareos-fd.conf 
Job {
  Name = "backup-bareos-fd"
  JobDefs = "DefaultJob"
  Client = "bareos-fd"
}

## jobdef中配置
root@johnny_server:/usr/local/etc/bareos/bareos-dir.d/jobdefs# cat DefaultJob.conf 
JobDefs {
  Name = "DefaultJob"
  Type = Backup
  Level = Incremental
  Client = bareos-fd
  FileSet = "SelfTest"                     # selftest fileset
  Schedule = "WeeklyCycle"
  Storage = File # S3_Object
  Messages = Standard
  Pool = Incremental
  Priority = 10
  Write Bootstrap = "/usr/local/var/lib/bareos/%c.bsr"
  Full Backup Pool = Full                  # write Full Backups into "Full" Pool
  Differential Backup Pool = Differential  # write Diff Backups into "Differential" Pool
  Incremental Backup Pool = Incremental    # write Incr Backups into "Incremental" Pool
}

## Storage配置
root@johnny_server:/usr/local/etc/bareos/bareos-dir.d/storage# cat File.conf 
Storage {
  Name = File
  Address = johnny_server                # N.B. Use a fully qualified name here (do not use "localhost" here).
  Password = ""
  Device = FileStorage
  Media Type = File
}
```

