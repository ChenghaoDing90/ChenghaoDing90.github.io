---
title: Trace
author: Chenghao Ding
layout: post
---

1. 矩阵的迹是特征值之和
2. 线性算子 $tr(mA+nB) = mtr(A)+ntr(B)$
3. $tr(A) = tr(A^\top)$
4. 循环性质
    - $tr(ABC) = tr(BCA) = tr(CAB)$
    - 更特殊的，若所有矩阵都是相同维度的对称矩阵，即$A, B, C \in S^n$，则在任何置换下保持不变
    $tr(ABC) = tr(BCA) = tr(CAB) = tr(ACB) = tr(BAC) = tr(CBA)$
5. 迹的导数
    $\frac{\partial tr(X)}{\partial X} = I$
