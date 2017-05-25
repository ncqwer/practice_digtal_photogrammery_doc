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
> - _minDisparity:
> - _numberOfDisparities:
> - _SADWindowSize:
> - _preFilterCap:
> - _uniquenessRatio:
> - _P1:
> - _P2:
> - _speckleWindowSize：
> - _speckleRange:
> - _disp12MaxDiff:
> - _fullDP:

#### SGBM::minDisparity
``` c++
SGBM& SGBM::minDisparity(
            const int m);
```
作用：
参数说明：
> - 
> - 

#### SGBM::numDisparities
``` c++
SGBM& SGBM::numDisparities(
        const int n);
```
作用：
参数说明：
> - 
> - 

#### SGBM::SADWindowSize
``` c++
SGBM& SGBM::SADWindowSize(
        const int sad);

```
作用：
参数说明：
> - 
> - 

#### SGBM::P1
``` c++
SGBM& SGBM::P1(
        const int p);
```
作用：
参数说明：
> - 
> - 

#### SGBM::P2
``` c++
SGBM& SGBM::P2(
        const int p);
```
作用：
参数说明：
> - 
> - 

#### SGBM::disp12MaxDiff
``` c++
SGBM& SGBM::disp12MaxDiff(
        const int d);
```
作用：
参数说明：
> - 
> - 

#### SGBM::preFilterCap
``` c++
SGBM& SGBM::preFilterCap(
        const int p);
```
作用：
参数说明：
> - 
> - 

#### SGBM::uniquenessRatio
``` c++
SGBM& SGBM::uniquenessRatio(
        const int u);
```
作用：
参数说明：
> - 
> - 

#### SGBM::speckleWindowSize
``` c++
SGBM& SGBM::speckleWindowSize(
        const int sz);
```
作用：
参数说明：
> - 
> - 

#### SGBM::speckleRange
``` c++
SGBM& SGBM::speckleRange(
        const int r);
```
作用：
参数说明：
> - 
> - 

#### SGBM::fullDP
``` c++
SGBM& SGBM::fullDP(
        const bool f);
```
作用：
参数说明：
> - 
> - 
