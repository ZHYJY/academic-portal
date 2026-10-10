# 学术检索链接平台（在线版）

一个可点击跳转的国内外学术检索数据库导航页。收录 142 个数据库（综合检索 / 期刊全文 / 学位论文 / 电子书古籍 / 预印本仓储 / 数据专利报告 / 医学 / 法律社科 8 大类），支持关键词搜索、地区与访问方式筛选，附国内外占比与分类构成图表。

## 文件说明

| 文件 | 作用 |
| --- | --- |
| `index.html` | 页面本体。部署后会自动在线加载 `data.json`；本地双击打开时自动使用内置兜底数据 |
| `data.json` | 数据库清单数据（唯一数据源）。**以后新增/修改数据库只需改这个文件** |
| `学术检索链接平台.html` | 纯本地版页面（不含在线加载逻辑），可删除或留作备份 |

## 部署到 GitHub Pages（约 10 分钟）

1. 登录 [github.com](https://github.com)，右上角 New repository 新建公开仓库（如 `academic-portal`）；
2. 将 `index.html`、`data.json`、`README.md` 三个文件上传到仓库根目录（仓库页面 Add file → Upload files，或本地 `git push`）；
3. 进入仓库 Settings → Pages → Source 选择 `Deploy from a branch`，Branch 选 `main` 与根目录 `/ (root)` → Save；
4. 等待 1–2 分钟构建完成，访问：
   `https://你的用户名.github.io/academic-portal/`
   （页面上的数据源徽标会显示「data.json（在线，更新即生效）」即部署成功）

## 如何更新

- 新增数据库：编辑 `data.json`，按下面的格式追加一条，保存后推送到 GitHub 仓库，线上页面自动更新，页面代码不用改：

```json
{
  "n": "数据库名称",
  "d": "一句话简介",
  "u": "https://官方链接",
  "r": "cn 或 intl",
  "a": "free 或 partial 或 login",
  "c": "comp / jour / thesis / book / preprint / data / med / law",
  "t": "可选标签，如 期刊全文"
}
```

字段说明：`r` 国内/国外；`a` 免费/部分免费/需登录；`c` 分类（综合学术搜索 / 期刊全文 / 学位论文 / 电子书与古籍 / 预印本与开放仓储 / 数据·专利·报告 / 医学与生命科学 / 法律与社会科学）。

- 常用入口：GitHub 网页上直接编辑 `data.json`（铅笔图标）→ Commit changes，即可完成更新，无需本地环境。

## 绑定自有域名（可选）

仓库 Settings → Pages → Custom domain 填入你的域名，并在 DNS 服务商添加 CNAME 记录指向 `你的用户名.github.io`，HTTPS 证书自动签发。

## 备选：Vercel 部署

登录 [vercel.com](https://vercel.com)（可用 GitHub 账号），New Project → Import 上述仓库 → Deploy，同样免费；更新时同样只需推送 `data.json`。

## 说明

- 国内访问 GitHub Pages 偶尔不稳定，长期使用可绑定域名或改用国内对象存储（腾讯云 COS / 阿里云 OSS 静态托管，量小基本免费）。
- 部分历史站点可能已改版或失效；b-ok.org 等版权争议站点已标注，请遵守所在地法律法规。
