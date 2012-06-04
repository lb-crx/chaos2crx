.. include:: ../LINKS.rst


+7分钟:初尝
==============

先通过最简单的插件,整起来,直觉的体验 `crx`_ 扩展开发的宏观流程先!

- 嗯嗯嗯,现在可以计时了:

00:00~安装
------------------------

- 下载 `猎豹浏览器`_ 最新公测版
- 安装

嗯嗯嗯,这个真心不用教了吧!

恭喜! 咱们已经获得了完整的 `开发/调试/运行/部署` 扩展的平台!



.. sidebar:: 提示

    不专门说明的话,指的都是笔者的个人环境:

      - MAC OS X 10.7
      - `Oracle VM VirtualBox <https://www.virtualbox.org/>`_ 最新版
      - DeepinXP 完美精简版 v5.8
      - `猎豹浏览器`_ v1.0.*



hello world
--------------------------------

著名的 `hello world <http://baike.baidu.com/view/47227.htm>`_ 是一定要整的,,,


那么在 `猎豹浏览器`_ 进行 `crx`_ 开发,有个比官网更加简单的例子,

来自: 魔方飛Young 的 `第一次做插件就献给了猎豹浏览器，一个简单的插件！（绝对原创） - 扩展插件区 - 猎豹浏览器官方论坛 <http://bbs.liebao.cn/thread-10640-1-13.html>`_


声明
^^^^^^^^^^^^

先开个目录,就叫: `halloworldliebao`

然后用任意文本编辑器,创立文件: `manifest.json` 内容如下

::

    { 
       "name": "Hallo World猎豹浏览器", 
       "version": "1.0", 
       "description": "魔方飛Young的第一个猎豹浏览器插件，还不错吧！", 
       "browser_action": { 
          "default_icon": "icon.gif", 
          "popup": "popup.html" 
       }
    }


图标
^^^^^^^^^^^^

再创建关键的:

.. _fig_0_1:
.. figure:: ../_static/figs/ch0-1-icon.gif

   插图.0-1 扩展的图标


当然,从官网抽个 icon 也成



完成
^^^^^^^^^^^^

好了准备工作完成! 正式开展编程!

- 先通过 `主菜单` -> `选项` -> `扩展程序` 进入管理界面

.. _fig_0_2:
.. figure:: ../_static/figs/ch0-2-devmod.png

   插图.0-2 打开"开发人员模式"

- 打开 `开发人员模式` 后,才能见到开发相关的功能
- 目前需要的只是: `载入正在开发的扩展程序`
- 然后就发觉,导航栏中,已经出现了刚刚扒到的图标,点击一下!?


.. _fig_0_3:
.. figure:: ../_static/figs/ch0-3-erro.png

   插图.0-3 点击图标时报错


- 嗯嗯嗯,出错了!
- 不过,不用怕,仔细看,是找不到 `popup.html` 页面,就是在 `manifest.json` 中指定的弹出页面嘛!
- 那么就地创建一个 `popup.html` 呗:

.. code-block:: html

    <p>Hello,World!</p>
    <p><a href="http://www.liebao.cn/" target="_blank">猎豹官网</a>
    <p><a href="http://bbs.liebao.cn" target="_blank">猎豹论坛</a>
    <p><img src="liebao.jpg" /></p>


- 然后, 点击 `重新载入` ,让 `猎豹浏览器`_ 重新加载修订后的扩展
- 再点击小豹子头?!

.. _fig_0_4:
.. figure:: ../_static/figs/ch0-4-done.png

   插图.0-4 点击图标时报错


**BINGO!**


07:01 小结
------------------------------

不出意外的话, 7分钟 用在这个阶段,太足够了!

应该已经体验到 `crx`_ 开发核心爽直了?!

- 只要具备 `JavaScript`_ 的编程经验,就可以进行任意扩展插件的开发了!
- 而且, 扩展的具体运行性能在 `V8`_  引擎以及 `Chromium`_ 卓越整合之下一点也不差!
- 以及, 先要习惯,并建立起,依托 `猎豹浏览器`_ 的 `crx`_ 扩展开发流程:

::

      加载本地开发中的扩展目录
        `->修订页面
            ^ `-> 重新加载
            |   `-> 测试扩展
            |           |
            +-----------/



