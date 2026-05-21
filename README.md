# 手机端饮食记录器

这是一个手机端饮食记录器，用来执行周期性饮食计划，而不是普通卡路里记账 App。

## 核心逻辑

- 食谱页负责设计饮食：设置每日目标、宏量比例、餐次分配、食材明细。
- 今日页负责打勾执行：照着当天食谱吃，吃了就点，记录饮水、补剂、状态和备注。
- 复盘页负责周期观察：查看执行率、平均热量、平均饮水、每周体重和腰围记录。

## 数据保存

数据保存在本机浏览器的 `localStorage` 中，当前存储 key 为：

```text
xh_diet_tracker_v3
```

后续更新 `index.html` 时，不要随便更改这个 key。只要 GitHub Pages 链接不变、localStorage key 不变、浏览器没有清除网站数据、用户没有换手机或换浏览器，已有饮食记录、食谱、食材库、周期设置和复盘数据一般会继续保留。

如果未来必须升级数据结构，需要写 migration 迁移逻辑：

- 检测旧数据是否存在。
- 自动补充新字段。
- 不覆盖旧记录。
- 不清空用户已有数据。

## 备份提醒

本工具支持导出 JSON 备份和导入 JSON 恢复。

请注意：

- 换手机、换浏览器、无痕模式、清除浏览器缓存或网站数据，可能导致数据丢失。
- 建议每周导出一次 JSON 备份。
- 每次大版本更新 `index.html` 前，建议先导出一次 JSON 备份。
- GitHub Pages 更新网页文件本身，一般不会删除 localStorage 数据。

## 静态部署

这是一个纯静态网页，只有 `index.html` 和 `README.md`，不依赖后端服务器。`index.html` 可以直接双击打开，也适合部署到 GitHub Pages。

GitHub Pages 部署方式：

1. 新建 GitHub 仓库。
2. 上传 `index.html` 和 `README.md`。
3. 进入仓库 `Settings`。
4. 打开 `Pages`。
5. `Source` 选择 `Deploy from a branch`。
6. `Branch` 选择 `main`。
7. `Folder` 选择 `/root`。
8. 点击 `Save`。

部署完成后，访问链接格式为：

```text
https://我的用户名.github.io/仓库名/
```
