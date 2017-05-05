## Repo file for MariaDB installation:
```
[mariadb]
name = MariaDB
baseurl=http://yum.mariadb.org/5.5/rhel7-amd64
# alternative: baseurl=http://archive.mariadb.org/mariadb-5.5.39/yum/rhel7-amd64/
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```

```
and placed this in /etc/yum.repos.d/MariaDB.repo
```