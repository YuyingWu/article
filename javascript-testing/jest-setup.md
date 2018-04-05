# Jest从入门到xx

> Delightful JavaScript Testing

在正式测试之前，给大家推荐一个拆箱即用的开发环境，基于`Parcel`、`Babel`和`Jest`。

```
git clone git@github.com:YuyingWu/jest-setup.git

npm install

// jest --watchAll
npm run test
```

这是个空项目，既没有程序代码也没有测试代码，所以第一次执行`npm run test`时，Jest会报错，提示没有测试用例。

## 第一个case

这个测试很简单，检验函数`hello`的返回结果是否`Hello, WYY`。

```
// App.js
export const hello = () => 'Hello, CBU';

// App.test.js
import { hello } from './App';

describe('hello', () => {
  test('should output: Hello, WYY', () => {
    expect(hello()).toBe('Hello, WYY');
  });
});
```

在测试文件`App.test.js`中，

* `describe(name, fn)`，声明测试套件，可包含多个测试用例
* `test(name, fn, timeout)`，声明一个测试用例，在里面写具体的测试逻辑（断言等）
* `expect` + `Matchers`（匹配器），检验函数返回值与期望值的匹配关系，常用Matchers包括`.toBe`、`.not.toBe`、`toContain`等。（更多方法见Jest官方文档[Using Matchers](https://facebook.github.io/jest/docs/zh-Hans/using-matchers.html)）

执行结果：
![](http://sinacloud.net/demo-static/article/jest-wrong-output.png)

不难看出，以上的测试，`hello`返回的值`Hello, CBU`与期待值`Hello, WYY`不一致，Jest的测试结果为`Fail`。

我改了一下：
```
// App.js
export const hello = () => 'Hello, WYY';
```

终于出现令人开心的小勾勾~

![](http://sinacloud.net/demo-static/article/jest-output-success.png)