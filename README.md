### 一


对于webpack项目修改打包后文件的引入，在package.json中添加
"homepage": "/github仓库名称"

就会修改打包后的产物
```
<link rel="stylesheet" href="/style.css">
为
<link rel="stylesheet" href="/github仓库名称/style.css">
```
<strong>如果不配置outDir,只需要把dist里的css,html，js一一放到github上就可以，
但是要选择github pages的根目录root，而不是docs目录</strong>



对于vite项目有种方式,修改打包后文件的引入
修改build命令
```
"build": "vite build --base=/github仓库名称"
```
<strong>如果不配置outDir,只需要把dist里的css,html，js一一放到github上就可以，
但是要选择github pages的根目录root，而不是docs目录</strong>



在vite.config.ts文件中添加
```
export default defineConfig({
  base:"/github仓库名/",
  build: {
    outDir: "docs",
  },
})
```
<strong>就可以将打包文件放到docs文件夹下，并且base路径为/github仓库名/
然后在github上的settings中的pages中设置docs文件夹为静态文件即可</strong>


### 二
执行npm i gh-pages -D
然后在vite.config.ts文件中添加
```
export default defineConfig({
  base:"/github仓库名/",
  build: {
    outDir: "build",
  },
})
```
base:"/github仓库名/",打包后的引入路径添加前置github仓库名
outDir: "build", 把dist文件夹改为build文件夹

执行npm run build

在package.json中添加
```
"scripts": {
    "deploy": "gh-pages -d build"
  },
```
执行npm run deploy







