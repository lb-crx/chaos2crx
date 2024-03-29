.. include:: ../LINKS.rst


金山云安全整备
============================

好的,俺想象的场景是:
- 每当打开一个页面时
- 俺的 `crx`_ 就将当前页面的 URL 发送给 `金山网址云 <http://code.ijinshan.com/api/devmore4.html#md1>`_
- 然后,根据返回的结论,决定,是否对页面进行刷红,并警告!


问题是看 `金山云安全开放平台 <http://code.ijinshan.com/api/devmore4.html#md2>`_ 的文档也是种挑战吼!
必须先研究一下!


简单的説
--------------------------

`金山网址云 <http://code.ijinshan.com/api/devmore4.html#md1>`_ 是个标准的接口服务

- 对钓鱼网站的查询,入口地址是 http://open.pc120.com/phish/
- 接受严密吻合要求的查询参数:

::

    /phish/?q=[***]&appkey=[***]&timestamp=[***]&sign=[***]
           |   |            |                |          +- 数字签字
           |   |            |                |          生成忒复杂,详见见下文
           |   |            |                +- 距离1970.1.1零点的秒数
           |   |            |                   要求精确到小数点后3位
           |   |            +- 从金山云申請到的
           |   +- 对目标URL进行 urlsafe base64 编码得到的字串
           +- 使用?引导出参数列表


- 一般从 `金山云安全开放平台 <http://code.ijinshan.com/api/>`_ 申請开发认证时,可以获得以下信息

::

  应用键(APPKEY): k-60666
  安全码(SECRET):  99fc9fdbc6761f7d898ad25762407373


- 那么,每次查询时,必须的 `数字签字` 是怎么生成的呢?
- 先组成这样一个字串

::

    /phish/?appkey=[APPKEY]&q=[***]&timestamp=[***][SECRET]
                      |         |               |   +- 安全码
                      |         |               +- 距离1970.1.1零点的秒数,精确到小数后3位
                      |         +- 对目标URL进行 urlsafe base64 编码得到的字串
                      +- 应用键值


- 然后,将此字串进行 `MD5`_ 计算! 得到的字串就是 `数字签名`
- 最后将整个 URL 拼到 http://open.pc120.com 后,直接访问,就可以获得 `JSON`_ 格式的回答
- 如果回答形如::

    {"success": 1, "phish ": 3} 

- 说明们成功了! 是否钓鱼网站参考:

.. list-table:: 类型表
   :widths: 10 30
   :header-rows: 1

   * - phish状态代号
     - 含义
   * - `-1`
     - 未知
   * - `0`
     - 非钓鱼
   * - `1`
     - 钓鱼
   * - `2`
     - 网站高风险,有钓鱼嫌疑




齐活儿! 这么大篇的技术文档,看穿了其实就以上这么点儿东西;-o

但是,怎么折腾成一个可用的 `crx`_ 呢?!




.. warning:: 

    - 走起!

