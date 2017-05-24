# absolute_orientation_kernal

## 模块说明
完成绝对定向

## API参考

#### Point
``` c++
typedef Eigen::Matrix<double,3,1> Point;
```
作用：3维坐标

#### absolute_orientation_kernal
``` c++
void absolute_orientation_kernal(
        const std::vector<Point>& model_pts,
        const std::vector<Point>& grand_pts,
        Eigen::Matrix<double,7,1>& paras,
        double& sigma_unti,
        Eigen::Matrix<double,7,1>& sigma_paras,
        std::vector<Eigen::Vector3d>& Vs);
```
作用：完成绝对定向
参数说明：
> - model_pts:模型坐标
> - grand_pts:地面坐标
> - paras:定向参数
> - sigma_unti:单位中误差
> - sigma_paras:各参数中误差
> - Vs:坐标残差

#### initial
``` c++
void initial(
        std::vector<Point>& model_pts,
        std::vector<Point>& grand_pts,
        Eigen::Matrix<double,7,1>& paras);
```
作用：中心化坐标并初始化定向参数
参数说明：
> - model_pts:模型坐标
> - grand_pts:地面坐标
> - paras:定向参数

#### update
``` c++
void update(
        Eigen::Matrix<double,7,1>& delta,
        Eigen::Matrix<double,7,1>& paras);
```
作用：迭代过程中更新定向参数
参数说明：
> - delta:定向参数的增量
> - paras:定向参数

#### isInTresh
``` c++
bool isInTresh(
        const Eigen::Matrix<double,7,1>& delta);
```
作用：判断定向参数的增量是否小于一定阈值
参数说明：
> - delta:定向参数的增量

#### calculate_R
``` c++
void calculate_R(
        const double phi,
        const double omega,
        const double kappa,
        Eigen::Matrix<double,3,3>& R);
```
作用：计算旋转矩阵R
参数说明：
> - phi:phi角
> - omega:omega角
> - kappa:kappa角
> - R:旋转矩阵R

#### calculate_A
``` c++
void calculate_A(
        const Point& model_pt,
        const Point& grand_pt,
        const Eigen::Matrix<double,7,1>& paras,
        const Eigen::Matrix<double,3,3>& R,
        Eigen::Matrix<double,3,7>& A);
```
作用：计算系数阵A
参数说明：
> - model_pts:模型坐标
> - grand_pts:地面坐标
> - paras:定向参数
> - R:旋转矩阵R
> - A:系数阵A

#### calculate_L
``` c++
void calculate_L(
        const Point& model_pt,
        const Point& grand_pt,
        const Eigen::Matrix<double,7,1>& paras,
        const Eigen::Matrix<double,3,3>& R,
        Eigen::Matrix<double,3,1>& L);
```
作用：计算常量L
参数说明：
> - model_pts:模型坐标
> - grand_pts:地面坐标
> - paras:定向参数
> - R:旋转矩阵R
> - L:常量L
