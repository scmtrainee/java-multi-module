README.md
```

configurations {
	unpackVelocity
	copy_dependencies{ transitive = false }
}


dependencies {
	unpackVelocity group: 'velocity', name: 'velocity', version: '1.5'
	copy_dependencies group: 'log4j', name: 'log4j', version: '1.2.4'
	copy_dependencies group: 'dom4j', name: 'dom4j', version: '1.6.1'
}


task getArtifacts(type:Copy){
	from(configurations.copy_dependencies){
		into 'dependency'
	}
	from(configurations.unpackVelocity.collect{it.isDirectory() ? it : zipTree(it)}){
		into "velocity"
		//exclude ${exclusion.velocity}
	}
	into "${buildDir}"
	includeEmptyDirs = false
}

/*
task unpackArtifacts(type: Copy){
	from(configurations.unpackVelocity.collect{it.isDirectory() ? it : zipTree(it)}){
		into "velocity"
		//exclude ${exclusion.velocity}
	}
	into "${buildDir}"
	includeEmptyDirs = false
}
*/

```