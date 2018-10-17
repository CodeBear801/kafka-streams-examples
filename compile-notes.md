# Notes

1. Compile issue: while compile schema-registry, met compile error like
```
[ERROR] [ERROR] Some problems were encountered while processing the POMs:
[FATAL] Non-resolvable parent POM for io.confluent:kafka-schema-registry-parent:[unknown-version]: Could not transfer artifact io.confluent:rest-utils-parent:pom:5.0.0 from/to confluent (${confluent.maven.repo}): Cannot access ${confluent.maven.repo} with type default using the available connector factories: BasicRepositoryConnectorFactory and 'parent.relativePath' points at wrong local POM @ line 7, column 13
 @ 
[ERROR] The build could not read 1 project -> [Help 1]
org.apache.maven.project.ProjectBuildingException: Some problems were encountered while processing the POMs:
[FATAL] Non-resolvable parent POM for io.confluent:kafka-schema-registry-parent:[unknown-version]: Could not transfer artifact io.confluent:rest-utils-parent:pom:5.0.0 from/to confluent (${confluent.maven.repo}): Cannot access ${confluent.maven.repo} with type default using the available connector factories: BasicRepositoryConnectorFactory and 'parent.relativePath' points at wrong local POM @ line 7, column 13
```
[solution]
Please do remember to checkout stable release version, for kafka its tags/v2.0.0, for others its tags/5.0.0

2. Operation issue: while restart confluent, met error below
```
Cannot start Schema Registry, Kafka Server is not running. Check your deployment
```

[solution]The issue was with the etc/schema-registry/schema-registry.properties file.
The line kafkastore.bootstrap.servers=PLAINTEXT://localhost:9092 was commented.


3. Operation issue: Leader Not Available Kafka in Console Producer

```
WARN Error while fetching metadata with correlation id 39 : 
     {4-3-16-topic1=LEADER_NOT_AVAILABLE} (org.apache.kafka.clients.NetworkClient)
```

[solution]go to server.properties and add
port = 9092
advertised.host.name = localhost 

4. Generate jar package
mvn compile -DskipTests
mvn package -DskipTests

5. Run the cases of confluent "Quick start manual"
   Word count
   WikipediaFeedAvroLambdaExample
   PageViewRegionLambdaExample
   WordCountInteractiveQueriesExample

