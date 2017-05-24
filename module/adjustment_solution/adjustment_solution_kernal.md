# adjustment_solution_kernal

## 模块说明
完成绝对定向

## API参考

#### Name
``` c++
template<typename UntiType, 
         typename BufferType, 
         std::size_t _num__one_until, 
         std::size_t _num_paras>
class AdjustmentSolution_kernal
{
public:
    typedef Eigen::Matrix<double,_num__one_until,_num_paras> TypeA;
    typedef Eigen::Matrix<double,_num__one_until,1> TypeL;
    typedef Eigen::Matrix<double,_num__one_until,1> TypeV;
    typedef Eigen::Matrix<double,_num_paras,1> TypeParas;

    typedef std::function<void(TypeA&,
                               const TypeParas&,
                               const UntiType&,
                               const BufferType&)> FuncTypeA;
    typedef std::function<void(TypeL&,
                               const TypeParas&,
                               const UntiType&,
                               const BufferType&)> FuncTypeL;
    typedef std::function<void(BufferType&,
                               const TypeParas&)> FuncTypeBuffer;
    AdjustmentSolution_kernal() {}
    ~AdjustmentSolution_kernal() {}

    AdjustmentSolution_kernal(const AdjustmentSolution_kernal& rhs) = delete;
    AdjustmentSolution_kernal(AdjustmentSolution_kernal&& rhs) = delete;

    AdjustmentSolution_kernal& operator= (AdjustmentSolution_kernal rhs_copy) = delete;
private:
    FuncTypeA _func_A;
    FuncTypeL _func_L;
    FuncTypeBuffer _func_buff;

    double _thresh=1 * 10e-6;

    std::size_t _max_num_iter = 10;

    TypeParas _paras;
    TypeParas _sigmas;
    BufferType _buffer_data;
    double _sigma_util;
    std::vector<TypeV> _Vs;

    std::vector<UntiType> _untis;
};

```
作用：
模板参数说明：
> - UntiType:平差基本单元的类型
> - BufferType:一次迭代过程中的不变量类型（用于加快平差计算）
> - _num__one_until:平差基本单元对应的残差数量
> - _num_paras:平差求解参数的个数
参数说明：
> - _func_A:用于计算系数阵A的函数
> - _func_L:用于计算常量L的函数
> - _func_buff:用于计算不变量buff的函数
> - _thresh:判断迭代过程中参数增量的绝对值是否过小的阈值 
> - _max_num_iter:允许的最大迭代次数
> - _paras:平差求解参数
> - _sigmas:各个参数的中误差
> - _buffer_data:不变量buff
> - _sigma_util:单位中误差
> - _Vs:残差
> - _untis:平差的基本单元的集合


### AdjustmentSolution_kernal::run
``` c++
AdjustmentSolution_kernal& 
    AdjustmentSolution_kernal::run()
```
作用：进行平差

### AdjustmentSolution_kernal::addUnti
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::addUnti(
        const UntiType& unti);
```
作用：添加平差单元
参数说明：
> - unti:平差基本单元

### AdjustmentSolution_kernal::addUnti
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::addUnti(
        const UntiType& unti);
```
作用：添加平差单元
参数说明：
> - unti:平差基本单元

### AdjustmentSolution_kernal::setFunc_A
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::setFunc_A(
        FuncTypeA func);
```
作用：设置用于计算系数阵A的函数
参数说明：
> - func:用于计算系数阵A的函数

### AdjustmentSolution_kernal::setFunc_L
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::setFunc_L(
        FuncTypeL func);
```
作用：设置用于计算常量L的函数
参数说明：
> - func:用于计算常量L的函数

### AdjustmentSolution_kernal::setFunc_Buffer
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::setFunc_Buffer(
        FuncTypeBuffer func);
```
作用：设置用于计算不变量buffer的函数
参数说明：
> - func:用于计算不变量buffer的函数

### AdjustmentSolution_kernal::setInitalValue
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::setInitalValue(
    const TypeParas& paras);
```
作用：设置平差参数的初始值
参数说明：
> - paras:平差参数的初始值

### AdjustmentSolution_kernal::data
``` c++
AdjustmentSolution_kernal& AdjustmentSolution_kernal::data(
        TypeParas& paras,
        double& sigma_util,
        TypeParas& sigmas,
        std::vector<TypeV>& Vs);
```
作用：返回平差结果
参数说明：
> - paras:平差参数
> - sigma_util:单位中误差
> - sigmas:各个参数的中误差
> - Vs:残差

### AdjustmentSolution_kernal::isInThresh
``` c++
bool AdjustmentSolution_kernal::isInThresh(
        const TypeParas &delta);
```
作用：判断定向参数的增量是否小于一定阈值
参数说明：
> - delta:定向参数的增量
