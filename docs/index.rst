=======================================
AutoReplyerのドキュメントへようこそ。
=======================================

.. warning::
    addコマンドなどで、条件や返信内容に空白を入れたい場合は `Discord.pyで対応しているクォート記号 <https://github.com/Rapptz/discord.py/blob/master/discord/ext/commands/view.py#L28-L46>`_ で囲む必要があります。
    クォートを無効化したい場合はクォートの直前にバックスラッシュを入れてください。

commands
==========

* :ref:`add`
* :ref:`remove`
* :ref:`reset`
* :ref:`list`


.. _add:

add
----------
自動返信を追加

.. warning::
    メッセージ管理の権限が必要です

::

    ar.add <条件> <返信内容> [オプション]?


.. csv-table::
    :header: "引数名", "必須かどうか", "特殊表現"
    :widths: 18, 9, 81 
    
    "条件", "Yes", "re, time, perfect, any, all"
    "返信内容", "Yes", "reaction, message, random"
    "オプション", "No", "なし"


.. _remove:

remove
----------
自動返信を削除

.. warning::
    メッセージ管理の権限が必要です

::

    ar.remove <識別方法> <識別内容>


.. csv-table::
    :header: "引数名", "必須かどうか", "選択肢(識別方法)", "エイリアス(識別方法)"
    :widths: 12, 18, 87, 90

    "識別方法", "Yes", "id / condition / replycontent", "識別子 / 条件, cnd / 返信内容, cnt, rc"
    "識別内容", "Yes", "", ""



.. _reset:

reset
----------
自動返信をすべて削除

.. warning::
    管理者の権限が必要です

::

    ar.reset



.. _list:

list
----------
自動返信のリストを表示


.. warning::
    ページは数字で指定してください


::

    ar.list <ページ>?


.. csv-table::
    :header: "引数名", "必須かどうか", "備考"
    :widths: 9, 18, 60

    "ページ", "No", "指定されたページが存在するページより大きい場合は一番最後のページが表示されます"



特殊表現
===============

**add**

* re
* time
* perfect
* any
* all
