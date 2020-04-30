README.md

```
test{
	ext.skipTests = project.hasProperty('skipTests') ? project.getProperty('skipTests') : false
	enabled = !(ext.skipTests.toBoolean())
	ignoreFailures = true
	//jvmArgs = $surefileArgLine
	exclude = '**/xyz*.java'
}
```
