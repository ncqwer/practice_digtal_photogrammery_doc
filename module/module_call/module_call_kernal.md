# module_call_kernal

## 模块说明：
规范化函数调用

## API 参考

#### moduleCall_kernal
``` c++
template <typename Func,
          typename... Args>
void moduleCall_kernal(
            const std::string& message,
            std::ostream& out,
            Func functor,
            Args&&... args);
```
作用: 规范化函数调用，实现记录函数运行时间

参数说明：
> - message:输出信息
> - out: 输出流
> - functor: 调用函数
> - args: 调用函数的参数
