- npm run sccipt 里得 各种工作流脚本
  一定要在跟目录
  1. dev 开发时运行的脚本
  2. start 启动服务器的脚本
    live-server
  3. build 开发完成后  一键build 生成上线文件
    压缩过后的
- wbepack bundle 打包工具  一切皆可打包
  1.webpack src/index.js dist/main.js
  2.webpack-cli 命令行工具
  3.webpack-dev-server 运行webpack编译的同时  启动8080端口  web-server

- html template
  1. css
  2. js

Error: Can't resolve './styles/normalize' in 'D:\work\webpack\dev_server\src'
该错误怎么解决？
在 webpack.config.js下
module.exports = {
    entry:'./src/index',
    output:{
        path:path.resolve(__dirname,'dist'),
        filename:'[name].js'   //[] 的意思是变量  原来的名字叫什么  他就会编译成什么名字
    },
    module:{
        rules:[
            {
                text:/\.css$/,
                use:['style-loader','css-loader']   //yarn add style-loader css-loader
            }
        ]
    },
    resolve:{
        extensions:['.css'],
        module:[
            path.resolve(__dirname,'node_modules')
        ]
    },


- resolve里 extensions 加后缀
  module里加 rules :[
      规则
      js->babel-loader->preset-env
      css->style-loader
      css-loader
      stylus->stylus
      stylus-loader
  ]

- 一切皆可打包  打包成为可运行的js 
  生成的文件  最好js css 分家
  一个文件  HTTP请求
  可以并发多个请求  拆成少数几个文件  js css 分离 这是必须做的
  
  webpack 样式的抽离