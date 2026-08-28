# Docker Manager Apps

Docker Manager Go 应用商店的数据源仓库。

结构对齐 1Panel appstore(https://github.com/1Panel-dev/appstore):

```
apps/
  <key>/
    data.yml          # 应用元数据(名称/描述/分类/官网)
    logo.png          # 应用图标
    README.md
    <版本号>/         # 每个版本一个目录
      docker-compose.yml   # compose 模板(${PANEL_XXX} 环境变量占位)
      data.yml             # 该版本参数表单(formFields)
      conf/ scripts/       # 附加配置与初始化脚本
```

面板运行时从本仓库同步应用数据(1Panel 同款机制),安装时解析 data.yml 生成参数表单,
把表单值注入 `${PANEL_XXX}` 环境变量渲染 compose 后部署。
