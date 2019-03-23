### 页面技术选型
为你的页面选择最优技术方案

PS: 有人看的话，我再加上具体demo，这个demo就相当于脚手架，可用于快速搭建业务，欢迎star和issue

### 渲染分类
这里渲染的意思是指html的动态生成。
1. 服务端渲染（server-side-render，ssr）
服务端渲染是把html的生成放在服务端，服务端直接返回完整的html，比如采用node搭建一个http服务，node接到请求后，根据条件获取数据库数据，
然后将数据应用到事先写好的模板，生成HTML，直接返回。
说明：简单交互一般是指页面只有些click，hover，简单列表更新的交互，复杂交互式一般包含列表翻页，复杂列表更新等
    * 简单交互服务端渲染：服务端渲染直出，页面逻辑交互用原生js。适合交互简单，但对首屏要求高的页面。
        * 优点：简单，首屏快，利于SEO
        * 缺点：服务端压力大
        * 线上例子：腾讯视频热榜(https://v.qq.com/x/hotlist/search)  
        * demo：demo/simple-reactive-ssr
        * 具体实现：node + ejs + 原生js，或者自己实现的一套基于字符串拼接的服务端渲染 + 原生js   
    * 复杂交互服务端渲染：采用同构方式，一套代码构建生成两端代码，用户请求时，服务端渲染出html页面，
    到客户端后，混合，进行事件绑定等，不在进行客户端渲染，可满足复杂交互，代码也利于维护。
        * 优点：首屏快，利于SEO，同构方式满足复杂交互，便于代码维护
        * 缺点：技术稍复杂，学习成本高
        * 线上例子：腾讯视频web搜索页(https://v.qq.com/x/search/?q=杨超越&stag=102&smartbox_ab=)  
        * demo：demo/complex-reactive-ssr
        * 具体实现：Vue同构，不过Vue的ssr是基于vdom的，没有字符串拼接的快，求尤大出一个
    * 单页服务端渲染：页面由服务端渲染，路由采用单页方式，不同的路由拉去不用页面片，采用这种渲染方式，交互与单页应用一样，但是每一个路由所得html
    由服务端生成，结合了单页应用和服务端渲染的双重优势
        * 优点：首屏快，利于SEO，单页路由方式大大提高用户体验
        * 缺点：技术复杂，学习成本高
        * 线上例子：腾讯视频大型h5商城(https://mall.video.qq.com/) 
        * demo：demo/single-page-based-ssr
        * 具体实现：有待开源
2. 客户端渲染（client-side-render，csr）
客户端渲染是把html的生成放在客户端，如浏览器
    * 简单交互客户端渲染
        * 优点：简单，简单，简单
        * 线上例子：这个很常见，就不举例子了
        * demo：demo/simple-reactive-csr
        * 具体实现：Vue，react，angular等框架，jQuery，或者原生js
    * 单页应用
        * 优点：简单，集合所有复杂业务到一个页面，方便运维
        * 缺点：首屏加载慢
        * 线上例子：一般用于内部管理台，有权限限制，不好给例子
        * demo：demo/single-page-application
        * 具体实现：Vue，react，angular等框架
