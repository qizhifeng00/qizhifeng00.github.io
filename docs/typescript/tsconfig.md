# Typescript

目前为止只有一个 TS 配置文件

## tsconfig.json

目前在用的配置文件

```json
{
  "compilerOptions": {
    "target": "esnext", // 目标语言的版本
    "useDefineForClassFields": true, //对类字段使用定义
    "module": "esnext", // 指定生成代码的模板标准
    "moduleResolution": "node", // 模块解析策略，ts默认用node的解析策略，即相对的方式导入
    "strict": true, // 开启所有严格的类型检查
    "checkJs": false, // 是否允许js
    "jsx": "preserve",
    "importHelpers": true, // 通过tslib引入helper函数，文件必须是模块
    "sourceMap": true, // 生成目标文件的sourceMap文件
    "resolveJsonModule": true, //允许导入带有“.json”扩展名的模块
    "esModuleInterop": true, // 允许export=导出，由import from 导入
    "baseUrl": "./", //基础路径
    "skipLibCheck": true, //跳过声明文件的类型检查
    "strictNullChecks": false, //严格Null检查
    "isolatedModules": true,
    "noUnusedLocals": true, // 检查只声明、未使用的局部变量(只提示不报错)
    "noUnusedParameters": true, // 检查未使用的函数参数(只提示不报错)
    "noImplicitAny": false, // 不允许隐式的any类型
    "noImplicitThis": false, // 不允许this有隐式的any类型
    "experimentalDecorators": true, //实验装饰器
    "allowSyntheticDefaultImports": true,
    "declaration": true, // 生成声明文件，开启后会自动生成声明文件
    "declarationDir": "es", // 指定生成声明文件存放目录
    "allowJs": true, // 允许编译器编译JS，JSX文件
    "types": ["@dcloudio/types", "node", "wechat-miniprogram"],
    "paths": {
      // 路径映射，相对于baseUrl
      "@/*": ["src/*"]
    },
    "lib": ["esnext", "dom", "es2017", "dom.iterable", "scripthost"]
  },
  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue"],
  "exclude": ["node_modules", "dist", "lib", "es"]
}
```
