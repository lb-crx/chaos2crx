.. include:: ../LINKS.rst


+20分钟:突入 页面动作 
============================


google 真心好朋友,通过搜索可以获得很多已经用上 `crx`_ 的先驱们的各种代码片段

只要使用 `改.js->测试` 流程,结合以往的开发经验,驗证猜想,突进就好!

- 嗯嗯嗯,现在可以计时了: 

07:05~ 确认阵地
------------------------------------



搞掂?!
------------------


`JS`_ 真心 `碉堡` 了! 所有最常见的操作都内置了!

- 字串的 `base64` 编码: `Buffer(uri).toString('base64')`
- 字串的 `md5` 编码: `crypto.createHash('md5').update(字串).digest("hex")`
- 当前时间戮只能先模拟小数点后的: `Date.parse(new Date())/1000+".512"`
- `POST` 上来的数据体 `req.body.uri`
- 实际数据的引用: `req.body.uri`
- JSON数据体的解析: `JSON.parse`


但是,怎么 `向外部url发出请求并接收数据?!`

- 之前选择框架时,已经可以使用 `http.get()` 获取外部数据了
- 问题是:

    - `简单问题: http.get() 如何同步返回給客户端? - CNode <http://club.cnodejs.org/topic/4f3b7ebdb43c3c846a062332>`_
    - `node.js`_ 是天生异步的!
    - 对外网的请求也是! 所以,发出请求后,就自然返回了
    - 数据接收完备后,才继续处理
    - 可素! 此时,客户的本次请求已经返回了! 没有可用的 i/o 句柄返回远端数据了吼!!!


测试输出如 :ref:`fig_1_4`

.. _fig_1_4:
.. figure:: ../_static/figs/http-get.png

   插图.1-4 http.get()的异步问题



URLfetch
^^^^^^^^^^^^^^^^^



.. warning:: (#_#)

    - 这里涉及异步I/O模型的理解和使用
    - 暂时可以使用以往的经验,配合相关的模块解决
    - 但是,实在应该找机会深入学习理解一下,,,
    


37:15 ~ 小结
---------------------------

~ 这一堆,二十分鈡,整出来不难吧?

想来:
- 其实,关键功能性行为代码,就8行

    - 其中7 行全部可以在google 中直接搜索到
    - 仅仅有一行,是需要学习新的工具,安装新的组件,学习新的文档,抄进来新的函式

- 其余,都是力气活儿

    - 只要别抄錯
    - 都是赋值,赋值,赋值,赋值,,,,

- 只要注意每一步,都使用 `console.log` 吼回来,测试确认无误,就可以继续前进了,,,

`这就是脚本语言的直觉式开发调试体验!`
