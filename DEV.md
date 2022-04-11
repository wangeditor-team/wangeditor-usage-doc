# 开发文档

本项目基于 gitbook 开发

## 启动项目

【注意】nodejs 切换到 v10 版本，否则运行会报错。

- git clone 项目
- 安装插件 `npm install`
- 启动 `npm run dev`

## 手动构建

- 运行 `npm run build`
- 结果输出到 `_book` 文件夹

## 发布

- 【注意】如果增加了新文件，发布之前一定要在本地运行 `npm run dev` ，以更新目录
- 提交代码到 `master` 分支，会触发 [github actions](https://github.com/wangeditor-team/wangeditor-usage-doc/actions)
- 等待 github actions 执行完成，重新访问页面即可

## 修改 gitbook 配置

- 修改 `book.json`
- 运行 `npm run gitbook-install`
- 重新启动，或重新构建
- 提交代码

------

## 坑

- `docs` 目录下，图片文件夹之前叫 `_images` ，但是在 github pages 中图片不显示，返回 404 。改成 `images` 就好了。可能是 `_` 开头的文件夹，下面的文件就不公开。
