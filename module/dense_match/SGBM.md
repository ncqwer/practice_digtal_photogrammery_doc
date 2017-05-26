# SGBM

## 模块说明
实现了SGBM算法，仿照OpenCV接口，可使用函数级联的方式设置相关参数

## API说明

#### SGBM
``` c++
class SGBM
{
public:
    enum { DISP_SHIFT=4, DISP_SCALE = (1<<DISP_SHIFT) };

    //! the default constructor
     SGBM();

    //! the full constructor taking all the necessary algorithm parameters
    SGBM(
            int minDisparity, 
            int numDisparities, 
            int SADWindowSize,
            int P1, int P2, int disp12MaxDiff, int preFilterCap,
            int uniquenessRatio, int speckleWindowSize, int speckleRange,
            bool fullDP );
    //! the destructor
    ~SGBM();

    int _minDisparity;
    int _numberOfDisparities;
    int _SADWindowSize;
    int _preFilterCap;
    int _uniquenessRatio;
    int _P1;
    int _P2;
    int _speckleWindowSize;
    int _speckleRange;
    int _disp12MaxDiff;
    bool _fullDP;

protected:
    cv::Mat buffer;
};

```
作用：存储SGBM算法过程中的关键数据和参数

参数说明：
> - _minDisparity:最小视差，默认值为 0, 可以是负值
> - _numberOfDisparities:视差窗口，即最大视差值与最小视差值之差, 窗口大小必须是 16 的整数倍
> - _SADWindowSize:SAD窗口大小，容许范围是[5,255]，一般应该在 5x5 至 21x21 之间，参数必须是奇数
> - _preFilterCap:预处理滤波器的截断值，预处理的输出值仅保留[-preFilterCap, preFilterCap]范围内的值
> - _uniquenessRatio:视差唯一性百分比， 视差窗口范围内最低代价是次低代价的(1 + uniquenessRatio/100)倍时，最低代价对应的视差值才是该像素点的视差，否则该像素点的视差为 0 
> - _P1:控制视差变化平滑性的参数。值越大，视差越平滑。P1是相邻像素点视差增/减 1 时的惩罚系数
> - _P2:控制视差变化平滑性的参数。值越大，视差越平滑。P2是相邻像素点视差变化值大于1时的惩罚系数
> - _speckleWindowSize：检查视差连通区域变化度的窗口大小
> - _speckleRange:视差变化阈值，当窗口内视差变化大于阈值时，该窗口内的视差清零
> - _disp12MaxDiff:左视差图和右视差图之间的最大容许差异
> - _fullDP:是否八方向

#### SGBM::minDisparity
``` c++
SGBM& SGBM::minDisparity(
            const int m);
```
作用：最小视差，默认值为 0, 可以是负值，int 型

参数说明：
> - m:最小视差

#### SGBM::numDisparities
``` c++
SGBM& SGBM::numDisparities(
        const int n);
```
作用：视差窗口，即最大视差值与最小视差值之差, 窗口大小必须是 16 的整数倍

参数说明：
> - n:视差窗口

#### SGBM::SADWindowSize
``` c++
SGBM& SGBM::SADWindowSize(
        const int sad);

```
作用：SAD窗口大小，容许范围是[5,255]，一般应该在 5x5 至 21x21 之间，参数必须是奇数，int 型

参数说明：
> - sad:SAD窗口大小

#### SGBM::P1
``` c++
SGBM& SGBM::P1(
        const int p);
```
作用：控制视差变化平滑性的参数。值越大，视差越平滑。P1是相邻像素点视差增/减 1 时的惩罚系数

参数说明：
> - p:控制视差变化平滑性的参数

#### SGBM::P2
``` c++
SGBM& SGBM::P2(
        const int p);
```
作用：控制视差变化平滑性的参数。值越大，视差越平滑。P2是相邻像素点视差变化值大于1时的惩罚系数

参数说明：
> - p:控制视差变化平滑性的参数

#### SGBM::disp12MaxDiff
``` c++
SGBM& SGBM::disp12MaxDiff(
        const int d);
```
作用：左视差图和右视差图之间的最大容许差异。

参数说明：
> - d:最大容许差异

#### SGBM::preFilterCap
``` c++
SGBM& SGBM::preFilterCap(
        const int p);
```
作用：预处理滤波器的截断值，预处理的输出值仅保留[-preFilterCap, preFilterCap]范围内的值

参数说明：
> - p:预处理滤波器的截断值

#### SGBM::uniquenessRatio
``` c++
SGBM& SGBM::uniquenessRatio(
        const int u);
```
作用：视差唯一性百分比， 视差窗口范围内最低代价是次低代价的(1 + uniquenessRatio/100)倍时，最低代价对应的视差值才是该像素点的视差，否则该像素点的视差为 0 

参数说明：
> - u:视差唯一性百分比

#### SGBM::speckleWindowSize
``` c++
SGBM& SGBM::speckleWindowSize(
        const int sz);
```
作用：检查视差连通区域变化度的窗口大小

参数说明：
> - sz: 窗口大小

#### SGBM::speckleRange
``` c++
SGBM& SGBM::speckleRange(
        const int r);
```
作用：视差变化阈值，当窗口内视差变化大于阈值时，该窗口内的视差清零

参数说明：
> - r:视差变化阈值

#### SGBM::fullDP
``` c++
SGBM& SGBM::fullDP(
        const bool f);
```
作用：当设置为 TRUE 时，进行8方向的，否则就进行5方向（0~4）

参数说明：
> - f: 是否八方向

#### SGBM::operator()
``` c++
void SGBM::operator()(
        cv::InputArray left, 
        cv::InputArray right,                                            cv::OutputArray disp);

```
作用:对左右影像进行SGBM调用，实际工作委托给sgbm.cpp中3个静态函数来完成

参数说明：
> - left:左图
> - right: 右图
> - disp: 视差图（实际上需要除以16） 
