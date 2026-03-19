# SimpleLedger GitHub Pages 部署指南

本目录用于承载简记账的法律文档与技术支持页面，适合直接部署到 GitHub Pages。

## 文件说明

- `index.html` - 法律与技术支持首页入口
- `privacy-policy.html` - 隐私政策
- `user-agreement.html` - 用户协议
- `support.html` - 技术支持
- `styles.css` - 站点共享样式

## 推荐访问结构

部署完成后，建议把首页作为默认入口：

- `https://your-github-username.github.io/simpleledger-policies/`

正文页面地址：

- `https://your-github-username.github.io/simpleledger-policies/privacy-policy.html`
- `https://your-github-username.github.io/simpleledger-policies/user-agreement.html`
- `https://your-github-username.github.io/simpleledger-policies/support.html`

## 部署步骤

### 1. 创建 GitHub 仓库

创建一个公开仓库，例如：`simpleledger-policies`

### 2. 上传文件

```bash
cd github-pages
git init
git add index.html privacy-policy.html user-agreement.html support.html styles.css README.md
git commit -m "Add legal and support pages"
git branch -M main
git remote add origin https://github.com/your-github-username/simpleledger-policies.git
git push -u origin main
```

### 3. 启用 GitHub Pages

1. 打开仓库 `Settings`
2. 进入 `Pages`
3. `Source` 选择 `Deploy from a branch`
4. 选择 `main` 分支和根目录
5. 保存后等待几分钟生效

## 与 App 的关系

当前 App 已直接使用以下正文页地址：

- `privacy-policy.html`
- `user-agreement.html`

因此部署时请保留这两个文件名不变，避免影响现有 WebView 加载逻辑。

新增的 `index.html` 主要用于：

- 对外公开访问时作为首页入口
- 后续扩展更多文档页面时统一承载入口
- 未来若 App 增加“法律与支持中心”入口时直接复用

## 当前联系邮箱

- `lurencha_developer@163.com`

如需更换邮箱，请同步修改：

- `index.html`
- `privacy-policy.html`
- `user-agreement.html`
- `support.html`

## 更新文档

修改页面后，重新提交并推送即可：

```bash
git add .
git commit -m "Update legal and support pages"
git push
```

## 发布前检查

运行：

```bash
bash ../scripts/check-github-pages-legal-site.sh
```

建议再手工检查：

- 首页可正常打开
- 首页到三页的跳转正确
- 三页都能返回首页
- 三页之间互链正常
- 手机端无横向滚动
- `mailto:` 邮件链接可点击
- App 内 WebView 能正常加载正文页
