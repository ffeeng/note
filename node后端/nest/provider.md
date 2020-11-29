[TOC]

## Provider类型

```typescript
export type Provider<T = any> =
  | Type<any>
  | ClassProvider<T>
  | ValueProvider<T>
  | FactoryProvider<T>
  | ExistingProvider<T>;
```

## ClassProvider

```typescript
export interface ClassProvider<T = any> {
  /**
   * Injection token
   */
  provide: string | symbol | Type<any> | Abstract<any> | Function;
  /**
   * Type (class name) of provider (instance to be injected).
   */
  useClass: Type<T>;
  /**
   * Optional enum defining lifetime of the provider that is injected.
   */
  scope?: Scope;
}


const configServiceProvider = {
  provide: ConfigService,
  useClass:
    process.env.NODE_ENV === 'development'
      ? DevelopmentConfigService
      : ProductionConfigService,
}
```

## ValueProvider

```typescript
export interface ValueProvider<T = any> {
  /**
   * Injection token
   */
  provide: string | symbol | Type<any> | Abstract<any> | Function;
  /**
   * Instance of a provider to be injected.
   */
  useValue: T;
}

const connectionProvider = {
  provide: 'CONNECTION',
  useValue: connection,
};
```

## FactoryProvider

```typescript
export interface FactoryProvider<T = any> {
  /**
   * Injection token
   */
  provide: string | symbol | Type<any> | Abstract<any> | Function;
  /**
   * Factory function that returns an instance of the provider to be injected.
   */
  useFactory: (...args: any[]) => T;
  /**
   * Optional list of providers to be injected into the context of the Factory function.
   */
  inject?: Array<Type<any> | string | symbol | Abstract<any> | Function>;
  /**
   * Optional enum defining lifetime of the provider that is returned by the Factory function.
   */
  scope?: Scope;
}

const connectionFactory = {
  provide: 'CONNECTION',
  useFactory: (optionsProvider: OptionsProvider) => {
    const options = optionsProvider.get();
    return new DatabaseConnection(options);
  },
  inject: [OptionsProvider],
};
```

## ExistingProvider

```typescript
export interface ExistingProvider<T = any> {
  /**
   * Injection token
   */
  provide: string | symbol | Type<any> | Abstract<any> | Function;
  /**
   * Provider to be aliased by the Injection token.
   */
  useExisting: any;
}

const loggerAliasProvider = {
  provide: 'AliasedLoggerService',
  useExisting: LoggerService
};
```

## 参考

[nest源码](https://github.com/nestjs/nest/blob/master/packages/common/interfaces/modules/provider.interface.ts)

