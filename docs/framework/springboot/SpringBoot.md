# springBoot

## SpringBoot相关面试题

### Spring,Spring MVC,Spring Boot 之间什么关系?

 Spring 包含了多个功能模块（上面刚刚提高过），其中最重要的是 Spring-Core（主要提供 IoC 依赖注入功能的支持） 模块， Spring 中的其他模块（比如 Spring MVC）的功能实现基本都需要依赖于该模块。 

 Spring MVC 是 Spring 中的一个很重要的模块，主要赋予 Spring 快速构建 MVC 架构的 Web 程序的能力。MVC 是模型(Model)、视图(View)、控制器(Controller)的简写，其核心思想是通过将业务逻辑、数据、显示分离来组织代码。 

Spring Boot则是为了简化使用 Spring 进行开发各种配置过于麻烦的问题而诞生的，比如开启某些 Spring 特性时，需要用 XML 或 Java 进行显式配置。如果说Spring 旨在简化 J2EE 企业应用程序开发，那么Spring Boot就是旨在简化 Spring 开发（减少配置文件，开箱即用！）。如果我们需要构建 MVC 架构的 Web 程序，还是需要使用 Spring MVC 作为 MVC 框架，只是说 Spring Boot 帮助简化了 Spring MVC 的很多配置，真正做到开箱即用！

### 什么是 SpringBoot 自动装配？如何实现的？

 没有 Spring Boot 的情况下如果需要引入第三方依赖，就需要手动配置，非常麻烦。但是Spring Boot 中，我们直接引入一个 starter 即可。比如你想要在项目中使用 redis 的话，直接在项目中引入对应的 starter 即可。 这种自动配置装载的功能就是自动装配，也就是说可以简单理解为：**通过注解或者一些简单的配置就能在 Spring Boot 的帮助下实现某块功能。** 

 要知道自动装配的实现原理，首先要看一下 SpringBoot 的核心注解 `SpringBootApplication` 。 `@SpringBootApplication`可以看作是 `@Configuration`、`@EnableAutoConfiguration`、`@ComponentScan` 注解的集合。根据 SpringBoot 官网，这三个注解的作用分别是：

- `@EnableAutoConfiguration`：启用 SpringBoot 的自动配置机制
- `@Configuration`：允许在上下文中注册额外的 bean 或导入其他配置类
- `@ComponentScan`： 扫描被`@Component` (`@Service`,`@Controller`)注解的 bean，注解默认会扫描启动类所在的包下所有的类 ，可以自定义不扫描某些 bean。

在Spring程序main方法中添加@SpringBootApplication或者@EnableAutoConfiguration后，程序会自动去maven中读取每个starter中的spring.factories文件，该文件里配置了所有需要被创建的Spring容器中的bean。