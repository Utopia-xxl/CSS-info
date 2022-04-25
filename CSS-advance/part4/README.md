# 安装并使用SCSS

1. 官网下载安装 node
2. Nom init 初始化项目
3. 安装node-sass`npm install node-sass --save-dev`
4. 取package.json文件中添加脚本，自动编译scss到css
   1. `"compile:sass": "node-sass sass/main.scss css/style.css"`配置好后执行`npm run compile:sass`即可将scss文件自动编译到配置好路径的css文件
   2. `"compile:sass": "node-sass sass/main.scss css/style.css -w"`添加-w 属性，终端会实时运行监测scss文件一旦保存修改就会自动编译

相关的代码在part3中