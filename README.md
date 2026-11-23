# scrubshot-lzcapp

Scrubshot 的 LazyCat 打包仓库。本仓库只存储打包配置，上游源码在 [strugglesky/scrubshot](https://github.com/strugglesky/scrubshot)。

## 结构

- `package.yml`：包元数据
- `lzc-manifest.yml`：运行结构（静态站，nginx 80 端口）
- `lzc-build.yml`：构建配置
- `.github/lazycat-action.yml` + `.github/workflows/lazycat.yml`：镜像模式自动化发布（指向 `ghcr.io/dockers-x/scrubshot`）

## 镜像来源

镜像由 [dockers-x/scrubshot](https://github.com/dockers-x/scrubshot) 工作流自动构建（不存上游代码，定时锁定上游 main 的 commit sha 构建 `linux/amd64,linux/arm64` 多架构镜像）。本仓库用 mutable `latest` + digest 基线跟踪：镜像变化时自动 bump patch 版本、更新 manifest 镜像引用并发布到喵喵商店。
