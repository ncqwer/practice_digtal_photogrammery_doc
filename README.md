# Introduction

## 开发环境
- os: ubuntu16.04
- 构建工具：cmake
- 编译工具:gnu
- 依赖的库：
    + OpenCV2.0
    + ceres(平差优化)
    + Eigen3(矩阵计算)
    + Gitbook(可选，用于生成api文档)
- 代码管理：Git

## practice_digital_photogrammetry 结构说明
- modulue
    + absolute_orientation
    + adjustment_solution
    + dense_match
    + module_call
- 相关头文件

其中：（以absolute_orientation为例）

- absolute_orientation_kernal: 一种实现
- absolute_orientation_kernal_1: 另一种实现

## 作业提交
下载解压文件
``` bash
mkdir build
cd build
cmake ..
make
```
在build/work文件夹下获得对应作业的答案，运行
``` bash
work/match # for work 4 
work/orientation # for work 2
```
## 贡献代码地址

[https://github.com/ncqwer/practice_digtal_photogrammery/tree/dev](https://github.com/ncqwer/practice_digtal_photogrammery/tree/dev)

## 文档地址
[https://www.gitbook.com/book/ncqwer/practice_digtal_photogrammery_doc/details](https://www.gitbook.com/book/ncqwer/practice_digtal_photogrammery_doc/details)

## 文档贡献地址

[https://github.com/ncqwer/practice_digtal_photogrammery_doc/tree/dev](https://github.com/ncqwer/practice_digtal_photogrammery_doc/tree/dev)