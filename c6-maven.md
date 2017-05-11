### 常用命令：

```
mvn clean package -Dmaven.test.skip=true -P beta
mvn clean assembly:assembly -Dmaven.test.skip=true
```

## maven 插件

assembly插件

```
<build>
	<plugins>
		<plugin>
			<artifactId>maven-assembly-plugin</artifactId>
			<configuration>
				<descriptors>
					<descriptor>src/main/assembly/descriptor.xml</descriptor>
				</descriptors>
			</configuration>
			<executions>
				<execution>
					<id>make-assembly</id>
					<!-- this is used for inheritance merges -->
					<phase>package</phase>
					<!-- bind to the packaging phase -->
					<goals>
						<goal>single</goal>
					</goals>
				</execution>
			</executions>
		</plugin>
	<plugins>
	<finalName>${project.artifactId}</finalName>
</build>
```



