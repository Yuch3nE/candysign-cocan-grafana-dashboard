# 制糖工厂 · AI⼩电拼 · 运行总览

小电拼 2264（CP-02S）的 Grafana 运行总览仪表盘，覆盖充电输出、端口状态、系统负载、内存、网络质量和用电量等信息。

![Grafana IonBridge Dashboard 预览](./grafana-ionbridge-preview.png)

## 文件

- [`grafana-ionbridge-dashboard.json`](./grafana-ionbridge-dashboard.json)：Grafana 仪表盘导出文件。
- [`grafana-ionbridge-preview.png`](./grafana-ionbridge-preview.png)：仪表盘预览图。

## 仪表盘信息

| 项目 | 值 |
| --- | --- |
| 标题 | 制糖工厂 · AI⼩电拼 · 运行总览 |
| UID | `ionbridge` |
| 默认时间范围 | 最近 3 小时（`now-3h` 至 `now`） |
| 自动刷新 | 10 秒 |
| 数据源 | Prometheus（`${DS_PROMETHEUS}`） |
| 设备筛选 | `instance`，基于 `ionbridge_uptime_seconds` 标签值 |
| 标签 | `CANDYSIGN`、`ionbridge`、`小电拼`、`CP-02S` |

## 监控内容

- 顶部概览：当前总功率、CPU 忙碌、活跃充电口、运行时间、Wi‑Fi 信号和可用堆内存。
- 端口监控：端口功率趋势、端口状态、端口电压和端口电流。
- 用电统计：所选时段用电量、每小时用电量和各端口用电量；端口用电量按返回的端口编号稳定排序。

## 导入 Grafana

1. 打开 Grafana 的 **Dashboards → Import**。
2. 上传 `grafana-ionbridge-dashboard.json`。
3. 在导入页面将 `${DS_PROMETHEUS}` 绑定到实际的 Prometheus 数据源。
4. 导入后选择对应的 `instance`，并根据需要调整时间范围或刷新频率。

## 数据要求

Prometheus 需要能够抓取 IonBridge / CP-02S 暴露的指标，并提供 `instance` 标签。仪表盘中的实时数值取决于 Prometheus 当前数据；README 中的预览图仅用于展示布局和样式。
