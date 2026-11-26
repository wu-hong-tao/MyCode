# MyCode
# MyCode
QR解码流程图
mermaid
flowchart LR
    classDef nodeStyle font-size:26pt,font-weight:bold,stroke-width:2px
    A[输入图像]:::nodeStyle ==> B[灰度化 + 高斯滤波]:::nodeStyle
    B ==> C[全局Otsu + 自适应阈值<br/>按位或融合]:::nodeStyle
    C ==> D[候选定位<br/>优先RLE，候选<3时轮廓兜底]:::nodeStyle
    D ==> E[三点定序 A/B/C]:::nodeStyle
    E ==> F[版本 N 估计]:::nodeStyle
    F ==> G[仿射 / 透视双路采样]:::nodeStyle
    G ==> H[矩阵Otsu二值化 + Timing打分]:::nodeStyle
    H ==> I[择优输出 N×N 模块矩阵]:::nodeStyle
    D -.-> J[失败：候选点<3 或 N越界]:::nodeStyle
    F -.-> J
    G -.-> J
    H -.-> J
