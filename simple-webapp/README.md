```
task war_two(type: War){
	classifier 'two'
	webInf{
		from 'src/main/webapp'
	}
}
```

```
task createExplodedWar(type: Copy) {
    into "target/deploy/directory"
    with war
} 
```