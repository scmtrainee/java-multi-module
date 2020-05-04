README.md

```
task copyExtraResources(type: Copy) {
	from('src/non-packaged-resources') {
		include '**/*.html'
		include '**/*.gif'
		//filter(ReplaceTokens, tokens: [version: '2.3.1'])
		exclude '**/*.txt'
	}
	into 'target/extra-resources'
}
```

```

task attachArtifact(type: Zip){
	archiveName = "project-extra-rsrcs.zip"
    destinationDir = file("target/")

    from "target/extra-resources"
}
```