README.md
```
ext {
	database_driver = "com.mysql.jdbc.Driver"
	database_url = "jdbc:mysql://localhost:3306/database?autoReconnect=true"
	database_username = "myusername"
	database_password = "mypassword"
}

```

```
test{
	ext.skipTests = project.hasProperty('skipTests') ? project.getProperty('skipTests') : false
	enabled = !(ext.skipTests.toBoolean())
	ignoreFailures = true
	//jvmArgs = $surefileArgLine
	exclude = '**/xyz*.java'
}
```
