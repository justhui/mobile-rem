#### 移动端适配方案初探

利用两个插件 postcss-pxtorem 和 amfe-flexible 
安装：
  + npm install amfe-flexible --save
  + npm install postcss-pxtorem --save-dev

amfe-flexible即lib-flexible插件，由于viewport单位得到众多浏览器的兼容，lib-flexible这个过渡方案已经可以放弃使用，不管是现在的版本还是以前的版本，都存有一定的问题。建议大家开始使用viewport来替代此

#### 插件的作用
1. postcss-pxtorem
该插件作为辅助工具，帮助我们自动进行计算，我们只要设置设计稿的宽度，即在根目录新建postcss.config.js文件，并进行配置；
```
module.exports = {
  "plugins": {
    "postcss-pxtorem": {
        rootValue: 37.5, // 根据设计图尺寸写，设计图是1920，就写192
        propList: ['*'], // 需要被转换的属性
        selectorBlackList: [] // 不进行px转换的选择器
    }
  }
}
```
2. amfe-flexible
满足不同屏幕的尺寸的适配，为lib-flexible的改良版本

# mobile-phone

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
