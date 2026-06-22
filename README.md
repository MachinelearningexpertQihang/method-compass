# 方法罗盘 · Method Compass

一个**数据分析方法选型**的交互式可视化工具。从五个维度描述你的问题，罗盘会用评分引擎给出**按拟合度排名的方法清单**，并附评估指标、常见坑、何时升级，以及一条完整的建模流水线。

> 定位：不替你跑数据，而替你理清"该用什么思路、哪个方法最合适"。

## 功能

- **五维定位**：目标 × 数据形态 × 样本规模 × 标签情况 × 首要诉求
  - 目标：回归 / 分类 / 聚类 / MMM / 因果 / 优化 / 时序 / 异常
  - 数据形态：表格 / 文本 / 图像 / 序列
  - 样本规模：小(<1k) / 中(1k–100k) / 大(>100k)
  - 标签情况：有标签 / 部分标签 / 无标签
  - 首要诉求：可解释 / 高性能 / 快速上线 / 鲁棒稳健
- **评分引擎**：内置 55+ 方法目录，每个方法带属性（可解释 / 性能 / 速度 / 鲁棒 / 小样本 / 大数据 / 是否需标签），按你的选择打分排名
- **排名候选**：输出 Top-4 方法 + 拟合度评分条，每个附常用库、评估指标、常见坑
- **完整流水线**：数据 → 特征 → 建模 → 评估 → 部署/解释，强调"模型只是其中一环"
- **路径可视化**：决策路径从「目标」一路点亮到「推荐方法」
- 覆盖工作向场景：**MMM 流水线**（adstock/saturation → 响应曲线 → 预算优化 → 实验校准）与**数学规划/优化**（LP / MIP / 凸优化）

## 技术栈

纯静态单文件，零依赖、零构建、零后端。字体走 Google Fonts CDN。

```
index.html   # 结构 + 样式 + 评分引擎 全在这一个文件里
```

> 推荐逻辑当前为**规则驱动**。后续可接 DuckDB-WASM + Polars：用户上传 CSV，浏览器内直接读取真实数据特征（行数、缺失率、类别基数、目标分布）来自动填充五个维度并驱动排名。

## 本地预览

直接双击 `index.html` 打开即可。或起本地服务器：

```bash
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000
```

## 部署到 GitHub Pages

1. 在 GitHub 新建一个 **public** 仓库，例如 `method-compass`
2. 把 `index.html`（和本 `README.md`）上传到仓库**根目录**
   - 网页端：**Add file → Upload files**，拖进去 Commit
   - 或命令行：
     ```bash
     git init
     git add .
     git commit -m "init: method compass"
     git branch -M main
     git remote add origin https://github.com/<你的用户名>/method-compass.git
     git push -u origin main
     ```
3. 仓库 **Settings → Pages → Source** 选 **Deploy from a branch**
4. Branch 选 **main**，文件夹 **/ (root)**，**Save**
5. 等 1–2 分钟，访问：`https://<你的用户名>.github.io/method-compass/`

## 备选部署（国内访问通常更快）

| 平台 | 操作 | 特点 |
|------|------|------|
| **Cloudflare Pages** | 连 GitHub 仓库 或 直接拖文件夹 | 免费、快、可绑自定义域名 |
| **Netlify** | 把文件夹拖进 netlify.com/drop | 最快上手，几秒上线 |
| **Vercel** | 导入 GitHub 仓库 | 一键部署 |

均为静态托管，**无需任何构建配置**——指到根目录、识别 `index.html` 即可。

## 许可

个人项目，自由使用。
