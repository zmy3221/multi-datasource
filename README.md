# Multi-DataSource项目
* Overview
  * 用于在多数据源之间切换
  * 依赖SpringBoot环境
* Useage
  1. 使用maven依赖该项目
  ```xml
  <dependency>
      <groupId>com.dover</groupId>
      <artifactId>multi-datasource</artifactId>
      <version>1.0.0</version>
  </dependency>
  ```
  2. 在application.properties/yml中配置多个数据源，以及其数据源name
  ```yml
  #multi-datasource config
  dover.multi.data-source-names[0]=datasource1
  dover.multi.data-source-names[1]=datasource2
  #datasource detail
  dover.multi.datasource1.driverClassName=com.mysql.jdbc.Driver
  dover.multi.datasource1.url=jdbc:mysql://localhost:3306/demo
  dover.multi.datasource1.username=xxx
  dover.multi.datasource1.password=yyy
  dover.multi.datasource1.initialSize=5
  dover.multi.datasource1.maxActive=10
  dover.multi.datasource1.minIdle=1
  dover.multi.datasource2.driverClassName=com.mysql.jdbc.Driver
  dover.multi.datasource2.url=jdbc:mysql://127.0.0.1:3306/test
  dover.multi.datasource2.username=xxx
  dover.multi.datasource2.password=yyy
  dover.multi.datasource2.initialSize=5
  dover.multi.datasource2.maxActive=10
  dover.multi.datasource2.minIdle=1
  ```
  3. 在 Bean **(必须实现了接口)** 上使用 `@SwitchDataSource("datasourceName")`来切换到已配置的某个数据源
  ```java
  @SwitchDataSource("datasource1")
  public class BridgeServiceImpl implements BridgeService { .. }
  ```