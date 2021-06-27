=======================================
AutoReplyerのドキュメントへようこそ。
=======================================


commands
==========

* :ref:`add`
* :ref:`remove`
* :ref:`list`
* :ref:`reset`

add
-----
自動返信を追加

.. warning::
    メッセージ管理の権限が必要です


構文::

    ar.add <条件> <返信内容> [オプション]?



.. csv-table::
    :header: "引数名", "必須かどうか", "特殊表現"
    :widths: 18, 9, 81 
    
    "条件", "Yes", "re, time, perfect, any, all"
    "返信内容", "Yes", "reaction, message, random"
    "オプション", "No", "なし"
