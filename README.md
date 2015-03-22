### Skinny Generator Example

```bash
brew install sbt
sbt "run db:migrate"
sbt "run generate:reverse-model-all"
```

### Result

```bash
$ sbt "run db:migrate"
[info] Loading project definition from /Users/seratch/Documents/gen-example/project
[info] Set current project to gen-example (in build file:/Users/seratch/Documents/gen-example/)
[info] Running TaskRunner db:migrate
2015-03-22 14:16:41,309 DEBUG [run-main-0] scalikejdbc.ConnectionPool$ Registered connection pool : ConnectionPool(url:jdbc:h2:file:./db/development;MODE=PostgreSQL;AUTO_SERVER=TRUE, user:sa) using factory : commons-dbcp2
2015-03-22 14:16:41,325 INFO [run-main-0] org.flywaydb.core.internal.util.VersionPrinter Flyway 3.2 by Boxfuse
2015-03-22 14:16:41,875 INFO [run-main-0] org.flywaydb.core.internal.dbsupport.DbSupportFactory Database: jdbc:h2:file:./db/development (H2 1.4)
2015-03-22 14:16:41,931 INFO [run-main-0] org.flywaydb.core.internal.command.DbValidate Validated 1 migration (execution time 00:00.023s)
2015-03-22 14:16:41,976 INFO [run-main-0] org.flywaydb.core.internal.command.DbMigrate Current version of schema "PUBLIC": 0
2015-03-22 14:16:41,977 INFO [run-main-0] org.flywaydb.core.internal.command.DbMigrate Schema "PUBLIC" is up to date. No migration necessary.
[success] Total time: 2 s, completed Mar 22, 2015 2:16:42 PM
$ sbt "run generate:reverse-model-all"
[info] Loading project definition from /Users/seratch/Documents/gen-example/project
[info] Set current project to gen-example (in build file:/Users/seratch/Documents/gen-example/)
[info] Running TaskRunner generate:reverse-model-all
2015-03-22 14:16:49,552 DEBUG [run-main-0] scalikejdbc.ConnectionPool$ Registered connection pool : ConnectionPool(url:jdbc:h2:file:./db/development;MODE=PostgreSQL;AUTO_SERVER=TRUE, user:sa) using factory : commons-dbcp2

 *** Skinny Reverse Engineering Task ***

  Table     : country
  ID        : id:Long

  Columns:
   - name:String:varchar(1000)
   - organizations:Seq[Organization]
   - persons:Seq[Person]

 *** Skinny Generator Task ***

  "src/main/scala/model/Country.scala" created.
  "src/test/scala/model/CountrySpec.scala" created.


 *** Skinny Reverse Engineering Task ***

  Table  : membership

  Columns:
   - organizationId:Option[Long]
   - personId:Option[Long]
   - createdAt:DateTime
   - organization:Option[Organization]
   - person:Option[Person]

 *** Skinny Generator Task ***

  "src/main/scala/model/Membership.scala" created.
  "src/test/scala/model/MembershipSpec.scala" created.


 *** Skinny Reverse Engineering Task ***

  Table     : organization
  ID        : id:Long

  Columns:
   - name:String:varchar(1000)
   - countryId:Long
   - url:Option[String]:varchar(1000)
   - createdAt:DateTime
   - country:Option[Country]
   - memberships:Seq[Membership]

 *** Skinny Generator Task ***

  "src/main/scala/model/Organization.scala" created.
  "src/test/scala/model/OrganizationSpec.scala" created.


 *** Skinny Reverse Engineering Task ***

  Table     : person
  ID        : id:Long

  Columns:
   - name:String:varchar(1000)
   - countryId:Long
   - createdAt:DateTime
   - country:Option[Country]
   - memberships:Seq[Membership]

 *** Skinny Generator Task ***

  "src/main/scala/model/Person.scala" created.
  "src/test/scala/model/PersonSpec.scala" created.

[success] Total time: 2 s, completed Mar 22, 2015 2:16:50 PM
```

