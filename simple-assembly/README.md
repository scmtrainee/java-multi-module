```
ext {
	artifact_finalName = 'my_assembly'
}

task makeAssembly_Batch(type: Tar){
	
	//archiveName "${artifact_finalName}" + '.tar'
	archiveName 'my_assembly.tar' // applies if plugin has <finalName>${artifact.finalName}</finalName>

	from ("src/main/scripts/fileReload.ksh"){
		into "reload-scripts"
	}

	from ("src/main/scripts/fileUpload.ksh"){
		into "upload-scripts"
	}

	from ("src/main/scripts"){
		into "utilities/scripts"
		include '**/*.ksh'
		exclude "fileUpload.ksh"
		exclude "fileReload.ksh"
	}

	from ("${project.projectDir}/../simple-weather/build/classes"){
		into 'weather-Batch/localconfig/'
		exclude "META-INF/**"
		exclude "pom.xml"
	}
	
	//into artifact_finalName // works with ${} notation or without.
	into 'my_assembly' // applies if <includeBaseDirectory> is true else ignore
}

```