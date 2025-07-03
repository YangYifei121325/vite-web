对于vite项目


2、修改打包文件
在vite.config.ts文件中添加
```
export default defineConfig({
  base:"/github仓库名/",
  build: {
    outDir: "docs",
  },
})
```
就可以将打包文件放到docs文件夹下，并且base路径为/github仓库名/

然后在github上的settings中的pages中设置docs文件夹为静态文件即可