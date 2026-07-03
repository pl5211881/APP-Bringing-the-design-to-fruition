# AI 学习报告原型

这是一个静态前端原型，用于还原「AI 学习报告」一级页与二级页流程。当前入口为 `index.html`，样式在 `styles.css`，图片和视频资源在 `assets/`。

## 在线预览

[点击查看 GitHub Pages 预览](https://pl5211881.github.io/APP-Bringing-the-design-to-fruition/)

## 本地运行

```bash
python3 -m http.server 4174
```

打开：

```text
http://127.0.0.1:4174/
```

也可以直接打开 `index.html` 预览，但推荐用本地服务，方便视频资源和后续动态接口联调。

## 资源说明

- `assets/`：页面运行所需图片、SVG、视频动效，建议随代码一起提交。
- `preview*.png`、`verify*.png` 等走查截图已通过 `.gitignore` 排除，不作为线上资源上传。

## 后续动态化建议

当前版本没有引入构建工具。后续如果要接入真实数据或做复杂交互，可以继续在当前仓库演进，也可以迁移到 Vite / React / Vue 等框架。迁移时建议保留：

- 页面状态流转：未生成、生成中、已生成、检测结果页。
- `assets/` 资源路径和命名。
- 底部按钮与 touchbar 的吸底逻辑。
- 移动端 414 设计稿等比适配逻辑。

## GitHub Pages

如果部署到 GitHub Pages，选择 `main` 分支根目录即可。`.nojekyll` 用于避免 GitHub Pages 对静态资源做 Jekyll 处理。
