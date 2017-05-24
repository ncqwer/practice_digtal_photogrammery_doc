# absolute_orientation_kernal_1

## 模块说明
通过adjustmemt_solution来完成绝对定向

## API参考

#### calculate_R_wrapper
``` c++
void calculate_R_wrapper(
        Eigen::Matrix<double,3,3>& R,
        const Eigen::Matrix<double,7,1>& paras);
```
作用：包装absolute_orientation_kernal模块中的calculate_R函数以满足adjustmemt_solution的接口要求
参数说明：
> - R:旋转矩阵R
> - paras:定向参数

#### calculate_A_wrapper
``` c++
void calculate_A_wrapper(
        Eigen::Matrix<double,3,7>& A,
        const Eigen::Matrix<double,7,1>& paras,
        const std::pair<Point,Point>& pt,
        const Eigen::Matrix<double,3,3>& R);
```
作用：包装absolute_orientation_kernal模块中的calculate_A函数以满足adjustmemt_solution的接口要求
参数说明：
> - A:系数阵A
> - pt:模型-地面点对
> - paras:定向参数
> - R:旋转矩阵R

#### calculate_L_wrapper
``` c++
void calculate_L_wrapper(
        Eigen::Matrix<double,3,1>& L,
        const Eigen::Matrix<double,7,1>& paras,
        const std::pair<Point,Point>& pt,
        const Eigen::Matrix<double,3,3>& R);
```
作用：包装absolute_orientation_kernal模块中的calculate_L函数以满足adjustmemt_solution的接口要求
参数说明：
> - L:常量L
> - pt:模型-地面点对
> - paras:定向参数
> - R:旋转矩阵R

#### absolute_orientation_kernal_1
``` c++
void absolute_orientation_kernal_1(
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
