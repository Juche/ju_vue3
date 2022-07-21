# Vue3 源码练习

## 流程

```sh
# 1. 初始化项目
pnpm init
# pnpm workspace 配置文件(必须指定 `.ymal`)
# 根目录新建 `pnpm-workspace.yaml` 文件
# 2. 添加依赖 & gitignore
# - w 参数指定依赖安装在工作空间更目录(add the dependency to the workspace root)
pnpm i esbuild minimist typescript -D -w
# 3. 初始化 ts 配置
# Creates a tsconfig.json with the recommended settings in the working directory.
pnpm tsc --init
```
