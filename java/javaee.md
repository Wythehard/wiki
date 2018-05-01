Java -jar check232.jar

brew install maven

项目目录下 mvn archetype:generate -DgroupId=city -DartifactId=cityapp -DarchetypeArtifactId=maven-archetype-webapp

pom.xml内容

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>city</groupId>
  <artifactId>cityapp</artifactId>
  <version>1.0-SNAPSHOT</version>
  <name>cityapp Maven Webapp</name>
  <url>http://maven.apache.org</url>
  <properties>
	  <commons-lang.version>2.6</commons-lang.version>
	  <slf4j.version>1.7.6</slf4j.version>
	  <spring.version>4.1.3.RELESE</spring.version>
  </properties>
  <dependencyManagement>
	  <dependencies>
		  <dependency>
		  <groupId>org.springframework</groupId>
		  <artifactId>spring-framework-bom</artifactId>
		  <version>${spring.version}</version>
		  <type>pom</type>
		  <scope>import</scope>
		  </dependency>
	  </dependencies>
  </dependencyManagement>
  <build>
    <finalName>cityapp</finalName>
  </build>
</project>

```





文件目录下运行项目 mvn jetty:run





自动生成ORM

java -jar mybatis-generator-core-1.3.5.jar -configfile generatorConfig.xml -overwrite