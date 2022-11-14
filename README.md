### 模块化方式

父模块起项目集合子模块作用，在父模块中使用<modules>标签指定子模块，在子模块中使用<parent>标签指定父模块，在子模块为实现实际逻辑模块。

- 父模块 pom.xml

```xml
  <groupId>seal.io</groupId>
  <artifactId>simple-java-maven-app</artifactId>
  <version>1.0-SNAPSHOT</version>
  <name>simple-java-maven-app</name>
  <!-- pom 打包方式代表父工程 -->
  <packaging>pom</packaging>

  <!-- 父模块包含子模块 -->
  <modules>
    <module>module1</module>
    <module>module2</module>
  </modules>

   <!-- 父模块包含依赖，其中log4j包含漏洞，这些依赖将会被子模块继承 -->
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <dependency>
      <groupId>org.apache.logging.log4j</groupId>
      <artifactId>log4j-core</artifactId>
      <version>2.12.2</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>4.3.30.RELEASE</version>
    </dependency>
  </dependencies>
```

- 子模块 Module1 pom.xml

```xml
  <!-- 父模块的GAV -->
  <parent>
    <groupId>seal.io</groupId>
    <artifactId>example-root</artifactId>
    <version>2.0-SNAPSHOT</version>
  </parent>

  <!-- 子模块pom，groupID和version使用父模块的 -->
  <artifactId>module1</artifactId>
  <name>module1</name>
```

- 子模块 Module2 pom.xml

```xml
  <!-- 父模块的GAV -->
  <parent>
    <groupId>seal.io</groupId>
    <artifactId>example-root</artifactId>
    <version>2.0-SNAPSHOT</version>
  </parent>

  <!-- 子模块pom，groupID和version使用父模块的 -->
  <artifactId>module2</artifactId>
  <name>module2</name>
```
