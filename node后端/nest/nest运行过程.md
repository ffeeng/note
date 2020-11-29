## 上下文对象

nest在启动时会初始化容器上下文，并创建好controller实例，当一个请求过来时，匹配相应的方法执行。

所以nest上下文对象一直驻留在内存中

上下文对象挂载到Server上面

在请求时
- req可以拿到socket,通过socket可以拿到server，通过server可以拿到上下文对象
- 路由信息放在 
  `socket._server._events.request._router.stack`



## 依赖注入过程

​      启动nest，

- bootstrap();

  调用nestFactory工厂创建app

- const app = await NestFactory.create(AppModule);

  初始化app

- await this.initialize(module, container, applicationConfig, httpServer);

  先扫描依赖，根据依赖创建实例，应用全局Providers

- ```
  await dependenciesScanner.scan(module);
  await instanceLoader.createInstancesOfDependencies();
  dependenciesScanner.applyApplicationProviders();
  ```

- await dependenciesScanner.scan(module);

  先注册核心模块，然后扫描模块，解析模块依赖

  ```
  await this.registerCoreModule();
  await this.scanForModules(module);
  await this.scanModulesForDependencies();
  this.addScopedEnhancersMetadata();
  this.container.bindGlobalScope();
  ```

- await instanceLoader.createInstancesOfDependencies();

  根据依赖创建实例

  ```
  async createInstancesOfDependencies() {
     const modules = this.container.getModules();
     this.createPrototypes(modules);
     await this.createInstances(modules);
  }
  ```

-  await this.createInstances(modules);

  创建实例，先创建Providers, 然后是Injectables ,接着是Controller
  
  ```
  async createInstances(modules) {
    await Promise.all([...modules.values()].map(async (module) => {
      await this.createInstancesOfProviders(module);
      await this.createInstancesOfInjectables(module);
      await this.createInstancesOfControllers(module);
      const { name } = module.metatype;
      this.isModuleWhitelisted(name) &&
      this.logger.log(messages_1.MODULE_INIT_MESSAGE `${name}`);
    }));
  }
  ```



## 请求执行过程

