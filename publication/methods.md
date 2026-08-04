# 方法

## 影像与头模型

MRI 数据来源：[填写]；扫描序列与参数：[填写]；头模型建立方法：[填写]；分割与网格审核：[填写]；DTI 数据来源与张量处理：[填写，是否受试者自身 DWI、采集参数、张量拟合与主方向提取方法]。

方法来源：[simnibs-charm]

## 有限元计算

采用 SimNIBS 4.6.0 有限元求解器（hypre），灰质分析含 1,337,567 个四面体。电导率按各向同性取值（白质 0.126、灰质 0.275、脑脊液 1.654、颅骨 0.010、头皮 0.465 S/m，来自 SimNIBS 会话文件；完整列表见参数记录），未纳入各向异性。

方法来源：[simnibs-methods]

## 海马定义

灰质单元中心变换至 MNI 标准空间后，以最近邻法采样 Harvard-Oxford 25% 最大概率图谱，定义左、右海马 ROI。

方法来源：[simnibs-methods], [violante-2023]

## TI 指标

两路载波 2.005 kHz 与 2.000 kHz 相差 5 Hz，叠加形成 5 Hz 低频包络。方向投影 TI 为电场沿纤维走向（DTI 主方向，几何近似）的包络分量，通常低于方向无关的 TImax；更换投影轴将改变全部数值。主要指标为方向投影 TI，TImax 作为补充；两者均为调制包络幅度，非神经激活阈值。

方法来源：[grossman-2017], [simnibs-methods]

## 区域统计

方向投影 TI 统计仅保留数值有效且体积为正的灰质单元；缺乏 DTI 方向的单元（10,425 个，约 3644.9 mm³）被排除并记为缺失。TImax 不依赖纤维方向，统计域包含全部灰质，故与方向投影 TI 的体积略有差异，表中“体积”列属方向投影 TI 有效域。均值、中位数与 P95 均按灰质体积加权；P99 高值区仅描述空间位置，非激活阈值。

方法来源：[tms-efield-review]

## 软件与复算

SimNIBS 4.6.0。方向投影 TI 与 TImax 用独立实现的公式逐单元复算，与 SimNIBS 输出最大绝对误差小于 1×10⁻¹² V/m（容差内一致）。该检查只验证公式一致性，不验证网格收敛；依赖版本与文件校验值见复核文件。

方法来源：[simnibs-methods]

## 参考文献

- [simnibs-charm] Puonti O et al. Accurate and robust whole-head segmentation from magnetic resonance images for individualized head modeling. NeuroImage. 2020;219:117044. https://doi.org/10.1016/j.neuroimage.2020.117044
- [simnibs-methods] Saturnino GB et al. SimNIBS 2.1: A comprehensive pipeline for individualized electric field modelling for transcranial brain stimulation. In: Brain and Human Body Modeling. 2019. https://doi.org/10.1007/978-3-030-21293-3_1
- [violante-2023] Violante IR et al. Non-invasive temporal interference electrical stimulation of the human hippocampus. Nature Neuroscience. 2023;26:1994-2004. https://doi.org/10.1038/s41593-023-01456-8
- [grossman-2017] Grossman N et al. Noninvasive deep brain stimulation via temporally interfering electric fields. Cell. 2017;169:1029-1041.e16. https://doi.org/10.1016/j.cell.2017.05.024
- [tms-efield-review] Dannhauer M, Gomez LJ, Robins PL, et al. Electric field modeling in personalizing TMS interventions. Biological Psychiatry. 2024;95:494-501. https://doi.org/10.1016/j.biopsych.2023.11.022
