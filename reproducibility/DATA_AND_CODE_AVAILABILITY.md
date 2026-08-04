# 数据与复核说明

## 可复算数据

本交付包包含报告使用的逐单元电场、分析区域掩膜、汇总表、图表支撑数据和发表图件。主要机器可读文件为 `../raw/ti_example_fields.h5`、`../raw/ti_example_fields.msh`、`../raw/ti_example_rois.msh`、`../packages/nifti_fields.zip` 及 CSV/Excel 结果表。

本例采用 SimNIBS 公共示例数据（示例受试者）和 Harvard-Oxford 皮层下 25% 最大概率图谱。上游解剖数据和图谱仍受各自分发条款约束，不作为本项目采集的受试者数据。参考文献用于界定 TI 指标和常见发表图表，不用于定义本项目身份或充当本例的数值基准。

## 软件环境

Python 和依赖版本记录在 `python_environment.json` 与 `requirements-lock.txt`。仿真参数、ROI 定义、计算口径和质量检查分别见 `../traceability/parameters.json` 与 `../traceability/quality_control.json`。

## 复核边界

基于现有派生有限元结果可重建报告、图表和区域统计。若完整重算有限元场，还需要 SimNIBS 公共示例头模型、原始求解会话、Harvard-Oxford 图谱及相同的软件环境。本例未进行网格收敛、电极位置扰动、组织电导率、分割、DTI 主方向、MNI 配准或跨受试者不确定性分析。

## 文件完整性

客户交付文件的字节数和 SHA-256 记录在 `../standard_manifest.json`；图件、图注和支撑数据的对应关系见 `../publication_index.json`。
