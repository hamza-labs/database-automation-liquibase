<a href="http://www.liquibase.org" ><img src='https://zohodiscussions.com/getCustomFile.do?fileId=49382000001011019&forumGroupId=49382000000003001' align='right' width='100'></a>

### :bar_chart:  Agile Database Automation With Liquibase  :bar_chart:
---------------

#### Introduction 
---------

Liquibase is an Open Source Solution for Agile Database Automation, we Integrate it with Jenkins CI & Maven Build to automate database Migrations.

#### Installation 
----------------

1. Install [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
2. Install [PostgreSQL Database PostgreSQL 9.5.3](http://get.enterprisedb.com/postgresql/postgresql-9.5.3-1-windows-x64.exe).
3. Install [Maven3.3.9](http://apache.mindstudios.com/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz).
4. Download [JDBC Driver](https://jdbc.postgresql.org/download/postgresql-9.4.1209.jre6.jar) & place it in Lib Folder.
5. Install [liquibase-3.5.1](https://github.com/liquibase/liquibase/releases/download/liquibase-parent-3.5.1/liquibase-3.5.1-bin.zip)
6. Add the directory containing the Liquibase.bat file to your PATH. 

#### Project Structure 

<p align="center">
<img src="https://raw.githubusercontent.com/elghoujdamilabs/database-automation/master/img/liquibase-project-structure.png" width='600' >
</p>

#### Local Development Process 
-----------------

Liquibase can be controlled via a Maven plug-in which can be obtained from the central Maven repository or can be run from the command line. 

##### 1. Database Migrations from commands line ( From an Empty Data To your-application-1.0 ) 

```
cd ./src/db 
```

```
liquibase --changeLogFile=changelog.master.xml --username=? --password=? --url=jdbc:postgresql://?:??/? --classpath=? --driver=org.postgresql.Driver update
```

##### 2. Generate Schema & Data from command line after Migrations if needed 

```
liquibase --changeLogFile=schema.postgresql.sql --username=? --password=? --url=jdbc:postgresql://?:?/? --classpath=? --driver=org.postgresql.Driver generateChangeLog
```

```
liquibase --changeLogFile=data.postgresql.sql --username=? --password=? --url=jdbc:postgresql://?:?/? --classpath=? --driver=org.postgresql.Driver  --diffTypes="data" generateChangeLog
```

##### 3. Database Migrations via Maven ( From an Empty Data To your-application-1.0 ) 

```  
mvn liquibase:update -Dliquibase.update -Dliquibase.changeLogFile=.\src\db\changelog.master.xml -Dliquibase.promptOnNonLocalDatabase=false -Dliquibase.url=jdbc:postgresql://?:?/? -Dliquibase.username=? -Dliquibase.password=? -Dliquibase.driver=org.postgresql.Driver 
```

##### 4. Generate Schema & Data via Maven after Migrations if needed 

```
mvn liquibase:update -Dliquibase.update -Dliquibase.changeLogFile=.\src\db\changelog.master.xml -Dliquibase.promptOnNonLocalDatabase=false -Dliquibase.url=jdbc:postgresql://?:?/? -Dliquibase.username=? -Dliquibase.password=? -Dliquibase.driver=org.postgresql.Driver 
```

##### 5. More About Liquibase Command Line (Liquibase Gists) 
- [Maintenance Commands](https://github.alliancelab.io/gist/a002527/2ba4233ba2ec51fd52033fba609ac926)
- [Database Update Commands](https://github.alliancelab.io/gist/a002527/2ba4233ba2ec51fd52033fba609ac926) 
- [Database Rollback Commands](https://github.alliancelab.io/gist/a002527/2ba4233ba2ec51fd52033fba609ac926) 
- [Diff Commands](https://github.alliancelab.io/gist/a002527/2ba4233ba2ec51fd52033fba609ac926) 
- [Documentation Commands](https://github.alliancelab.io/gist/a002527/2ba4233ba2ec51fd52033fba609ac926) 
