## gRPC

A sample project with gRPC-java. Refer to [grpc-java-tutorial](http://www.grpc.io/docs/tutorials/basic/java.html) for more details.


## Compile

gRPC server impls and stubs were generated by running `mvn clean compile`, utilizing the maven plugin: `org.xolstice.maven.plugins.protobuf-maven-plugin`:

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.xolstice.maven.plugins</groupId>
      <artifactId>protobuf-maven-plugin</artifactId>
      <version>0.5.0</version>
      <configuration>
        <!--
          The version of protoc must match protobuf-java. If you don't depend on
          protobuf-java directly, you will be transitively depending on the
          protobuf-java version that grpc depends on.
        -->
        <protocArtifact>com.google.protobuf:protoc:3.0.2:exe:${os.detected.classifier}</protocArtifact>
        <pluginId>grpc-java</pluginId>
        <pluginArtifact>io.grpc:protoc-gen-grpc-java:${grpc.version}:exe:${os.detected.classifier}</pluginArtifact>
        <protoSourceRoot>src/main/resources</protoSourceRoot>
        <outputDirectory>src/main/java/proto</outputDirectory>
        <clearOutputDirectory>true</clearOutputDirectory>
      </configuration>
      <executions>
        <execution>
          <goals>
            <goal>compile</goal>
            <goal>compile-custom</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```