# SEO 搜索引擎收录配置说明

> 网站域名：**https://car.yxjh.qzz.io**
>
> 最后更新：2026-06-29

---

## 📋 已完成工作清单

### 1. 基础 SEO 配置修改 ([_config.yml](file:///d:\wangzhan\yxjhcar\_config.yml))

| 配置项 | 修改内容 |
|--------|----------|
| `url` | `http://example.com` → `https://car.yxjh.qzz.io` |
| `keywords` | （原空）→ `卡丁车,卡丁车DIY,卡丁车教程,卡丁车改装,平衡车刷机,毅学就会` |

### 2. 添加 Sitemap 插件依赖 ([package.json](file:///d:\wangzhan\yxjhcar\package.json))

已添加两个插件：

```json
"hexo-generator-sitemap": "^3.0.1",      // 标准 sitemap.xml（Google、Bing 通用）
"hexo-generator-baidu-sitemap": "^0.1.9" // 百度专用 sitemap
```

### 3. 添加 Sitemap 配置到 [_config.yml](file:///d:\wangzhan\yxjhcar\_config.yml)

```yaml
sitemap:
  path: sitemap.xml
  rel: true
  tags: true
  categories: true

baidusitemap:
  path: baidusitemap.xml
```

### 4. 创建 robots.txt ([source/robots.txt](file:///d:\wangzhan\yxjhcar\source\robots.txt))

告诉搜索引擎哪些页面允许抓取：

```
User-agent: *
Allow: /
Allow: /archives/
Allow: /categories/
Allow: /tags/

Sitemap: https://car.yxjh.qzz.io/sitemap.xml
Sitemap: https://car.yxjh.qzz.io/baidusitemap.xml
```

---

## 🔧 你需要完成的工作

### 第一步：安装依赖

在项目根目录打开终端，执行：

```bash
npm install
```

这会安装上面添加的两个 sitemap 插件。

---

### 第二步：获取站点验证码并填写

主题已经预留了验证配置位置：**[themes/anzhiyu/_config.yml](file:///d:\wangzhan\yxjhcar\themes\anzhiyu\_config.yml)** 第 731-738 行

当前配置：

```yaml
site_verification:
  - name: google-site-verification # Google 搜索控制台验证
    content: xxx # 验证内容
  - name: baidu-site-verification # 百度站长平台验证
    content: code-xxx # 验证码
  - name: msvalidate.01 # Bing 站长工具验证
    content: xxx # 验证内容
```

> 你需要先完成**第三步（去各平台添加网站）**获取验证码，再把 `xxx`/`code-xxx` 替换成真实验证码。

---

### 第三步：去各搜索引擎平台提交网站

#### 🔵 百度搜索资源平台（优先做，国内主要搜索引擎）

**网址：** https://ziyuan.baidu.com/

**操作步骤：**

1. 打开网址，用百度账号登录（没有先注册）
2. 点击左上角 **「添加网站」**
3. 输入你的域名：`car.yxjh.qzz.io`，点击「下一步」
4. **选择验证方式：HTML 标签验证**
   - 百度会给你一段代码，类似：
     ```html
     <meta name="baidu-site-verification" content="code-abcdefghijklmn">
     ```
   - 把 `content=` 后面引号里的内容（这里就是 `code-abcdefghijklmn`）复制下来
5. 打开项目中的 `themes/anzhiyu/_config.yml`，找到上面的 `baidu-site-verification` 那一行，把 `code-xxx` 替换成你复制的验证码
6. 回到百度站长平台，点击「完成验证」
7. 验证成功后 → 左侧菜单 **「资源提交」** → **「sitemap」**
8. 输入：`baidusitemap.xml`，点击「提交」
9. （可选）同时去 **「普通收录」** → **「手动提交」**，提交首页 `https://car.yxjh.qzz.io/`

---

#### 🟢 Bing 网站站长工具（必应，同时覆盖 Yahoo 等）

**网址：** https://www.bing.com/webmasters/

**操作步骤：**

1. 打开网址，用 Microsoft 账号登录（没有先注册）
2. 点击 **「Add site」**（添加网站）
3. 输入你的域名：`https://car.yxjh.qzz.io`，点击「Add」
4. **验证方式选择：Meta tag**（HTML 元标记）
   - Bing 会给你类似：
     ```html
     <meta name="msvalidate.01" content="abcdef123456...">
     ```
   - 复制 `content=` 引号里的值
5. 打开项目中的 `themes/anzhiyu/_config.yml`，找到 `msvalidate.01` 那一行，把 `xxx` 替换成复制的值
6. 回到 Bing 站长平台，点击 **「Verify」**（验证）
7. 验证成功后 → 左侧菜单 **「Sitemaps」** → **「Add sitemap」**
8. 输入：`https://car.yxjh.qzz.io/sitemap.xml`，点击「Add」

---

#### 🔴 Google Search Console（可选，国内用户用得少）

**网址：** https://search.google.com/search-console/

**操作步骤：**

1. 打开网址，用 Google 账号登录
2. 点击 **「添加资源」**
3. 选择「网址前缀」，输入：`https://car.yxjh.qzz.io`，点击「继续」
4. **验证方式选择：「HTML 标记」**
   - Google 会给你类似：
     ```html
     <meta name="google-site-verification" content="abcdef123456...">
     ```
   - 复制 `content=` 引号里的值
5. 打开项目中的 `themes/anzhiyu/_config.yml`，找到 `google-site-verification` 那一行，把 `xxx` 替换成复制的值
6. 回到 Google Search Console，点击「验证」
7. 验证成功后 → 左侧菜单 **「站点地图」** → 输入 `sitemap.xml`，提交

---

### 第四步：重新生成并部署网站

完成验证码填写后，在终端执行：

```bash
hexo clean
hexo generate
hexo deploy
```

或者如果你用脚本：

```bash
npm run clean
npm run build
npm run deploy
```

> **说明**：`hexo clean` 清空旧的生成文件，`hexo generate` 生成新文件（会自动生成 `sitemap.xml` 和 `baidusitemap.xml`），`hexo deploy` 部署到服务器。

---

### 第五步：等待收录

| 搜索引擎 | 通常收录时间 |
|----------|-------------|
| 百度 | 1-4 周 |
| Bing | 1-7 天 |
| Google | 1-14 天 |

**收录加速建议：**
- 保持网站内容更新，定期发布新文章
- 可以在其他已收录网站给你这个网站加个友情链接
- 百度资源平台可以每日手动提交几个新链接

---

## 🔍 验证是否生成成功

部署后，在浏览器访问：

- https://car.yxjh.qzz.io/sitemap.xml → 应该能看到站点地图
- https://car.yxjh.qzz.io/baidusitemap.xml → 百度专用地图
- https://car.yxjh.qzz.io/robots.txt → 应该能看到 robots 内容

如果这三个都能正常访问，说明配置成功。

---

## 📝 配置文件修改总结

| 文件路径 | 修改内容 |
|----------|----------|
| `_config.yml` | 修改 `url`、填写 `keywords`、添加 `sitemap` 配置 |
| `package.json` | 添加两个 sitemap 依赖 |
| `source/robots.txt` | 新建，允许抓取并声明 sitemap |
| `themes/anzhiyu/_config.yml` | 需要手动填写 `site_verification` 验证码 |

---

## ❓ 常见问题

**Q: 提交了为什么搜索不到？**
> A: 搜索引擎收录需要时间，快则几天慢则几周，耐心等待。保持更新有助于加速。

**Q: 验证失败怎么办？**
> A: 检查验证码是否复制正确，替换后必须重新 `hexo generate` 再部署，然后刷新页面重新验证。

**Q: 一定要三个平台都提交吗？**
> A: 国内用户至少提交百度和 Bing，Google 可选，提交越多收录机会越多。