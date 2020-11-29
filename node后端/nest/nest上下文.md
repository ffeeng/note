[TOC]



## NestApplication应用程序

![image-20200915100945754](img/image-20200915100945754.png)

## NestContainer容器

![image-20200915104851524](img/image-20200915104851524.png)

## contextModule上下文模块

![image-20200915102528641](img/image-20200915102528641.png)

上下文模块，默认提供9个providers

- InternalCoreModule

- ModuleRef

- ApplicationConfig

- Reflector

- REQUEST

- INQUIRER

- ExternalContextCreator

- ModulesContainer

- HttpAdapterHost

```typescript
@Controller('v3')
export class GoodsController {

  constructor(
    private goodsService: GoodsService,

    @Inject('InternalCoreModule') private internalCoreModule,
    private moduleRef: ModuleRef,
    private applicationConfig: ApplicationConfig,
    private reflector: Reflector,
    @Inject('REQUEST') private req,
    // @Inject('INQUIRER') private inq,
    private creator: ExternalContextCreator,
    private container: ModulesContainer,
    private adapterHost: HttpAdapterHost,

  ) {
  }
} 
```

## ApplicationConfig配置

![image-20200915101637826](img/image-20200915101637826.png)

