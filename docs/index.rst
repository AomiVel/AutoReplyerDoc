=======================================
AutoReplyerのドキュメントへようこそ。
=======================================


**ドキュメントの修正案は常に受け付けています**


.. note::

    * `招待URL <https://discord.com/api/oauth2/authorize?client_id=856117107120668703&permissions=347200&scope=bot>`_
    * `サポートサーバー <https://discord.gg/r8SgQWW5Ha>`_


.. warning::
    * addコマンドなどで、条件や返信内容に空白を入れたい場合は `Discord.pyで対応しているクォート記号 <https://github.com/Rapptz/discord.py/blob/master/discord/ext/commands/view.py#L28-L46>`_ で囲む必要があります。
    * クォートを無効化したい場合はクォートの直前にバックスラッシュを入れてください。

bot
==========
Botについて

| デフォルトの接頭字: :code:`ar.`
| ※カスタムプレフィックス対応予定


commands
==========
各コマンドについて

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

    ar.add <条件> <返信内容> [オプション]


.. csv-table::
    :header: "引数名", "必須かどうか", "要素の数", "特殊表現"
    :widths: 18, 9,　12, 81 
    
    "条件", "Yes", "1", "re, time, perfect, any, all"
    "返信内容", "Yes", "1", "reaction, message, random"
    "オプション", "No", "可変", "なし"


.. note::
	特殊表現に関しては :ref:`uniqueexpression` を参考にしてください


.. _remove:

remove
----------
自動返信を削除

.. warning::
    メッセージ管理の権限が必要です

::

    ar.remove <識別方法> <識別内容>


.. csv-table::
    :header: "引数名", "必須かどうか", "要素の数", "選択肢(識別方法)", "エイリアス(識別方法)"
    :widths: 12, 18, 12, 87, 90

    "識別方法", "Yes", "1", "id / condition / replycontent", "識別子 / 条件, cnd / 返信内容, cnt, rc"
    "識別内容", "Yes", "1", "", ""



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
    :header: "引数名", "必須かどうか", "要素の数", "備考"
    :widths: 9, 18, 12, 60

    "ページ", "No", "1", "指定されたページが存在するページより大きい場合は一番最後のページが表示されます"


.. _uniqueexpression:

特殊表現
==========
addコマンドの特殊表現


条件
----------
条件の特殊表現

* :ref:`addre`
* :ref:`addtime`
* :ref:`addperfect`
* :ref:`addany`
* :ref:`addall`


.. _addre:

re
^^^^^^^^^^
正規表現を用いた条件の設定


.. note::
    正規表現の記入方法は `PythonDocument-re <https://docs.python.org/ja/3/library/re.html>`_ を参考にしてください


構文::

    re?<正規表現>



.. csv-table::
    :header: "引数名", "必須かどうか", "要素の数"
    :widths: 12, 18, 12

    "正規表現", "Yes", "1"


例文::

    re?こん(にちは)?
    "re?(?i)e(ven )?d(ead, )?i('m )? t(he )?h(ero )?"



.. _addtime:

time
^^^^^^^^^^
時間指定


.. note::
    タイムゾーンはJST(日本標準時)(UCT+9:00)です。

.. warning:: 
    * from時:-:to分
    * \:from分-to時\:
    * \:from分-from時\:to分
    * from時\:to分-\:to分
    
    これらのフォーマットは使用できません



構文::

    time?<from時>:<from分>-<to時>:<to分>


.. csv-table::
    :header: "引数名", "必須かどうか", "要素の数"
    :widths: 15, 18, 12

    "from時", "No", "1"
    "from分", "No", "1"
    "to時", "No", "1"
    "from分", "No", "1"


例文::

    time?12:-
    time?:30-
    time?-15:
    time?-:45
    time?12:30-
    time?-15:45
    time?12:-15:
    time?12:-15:45
    time?:30-:45
    time?12:30-15:
    time?12:30-15:45


.. _addperfect:

perfect
^^^^^^^^^^
完全一致


エイリアス: perf


構文::

    perfect?<文字列>
    perf?<文字列>



.. _addany:

any
^^^^^^^^^^
いずれかの条件が一致


.. warning::
    * 条件に空白を入れたい場合はシングルクォーテーション(')ではさむ必要があります。
    * この特殊表現はかならずダブルクォーテーション(")ではさむ必要があります


.. note::
    この特殊表現ではany, all以外のほかの特殊表現も使用できます



構文::

    "any(<条件1> <条件2> ...)"


例文::

    "any(hello こんにちは おはよう こんばんわ こんばんは)"
    "any(おはよう おはようございます 'good morning')"



.. _addall:

all
^^^^^^^^^^
すべての条件が一致


.. warning::
    * 条件に空白を入れたい場合はシングルクォーテーション(')ではさむ必要があります。
    * この特殊表現はかならずダブルクォーテーション(")ではさむ必要があります


.. note::
    この特殊表現ではany, all以外のほかの特殊表現も使用できます



構文::

    "all(<条件1> <条件2> ...)"


例文::

    "all(あ い う え お)"
    "all(おきた time?12:-)"



返信内容
----------
返信内容の特殊表現

* :ref:`addreaction`
* :ref:`addmessage`
* :ref:`addrandom`



.. _addreaction:

reaction
^^^^^^^^^^
リアクションを追加

エイリアス: react


構文::

    reaction?<絵文字>
    react?<絵文字>


例文::

    reaction?😆
    reaction?<a:server_emoji:642794020790925610>



.. _addmessage:

message
^^^^^^^^^^
メッセージの内容をそのまま送信

エイリアス: msg


構文::

    message?<メッセージURL>
    msg?<メッセージURL>


例文::

    message?https://discord.com/channels/702753450109696025/761265168854368406/888312814423857124



.. _addrandom:

random
^^^^^^^^^^
ランダムな返信内容

エイリアス: rand


構文::

    "random(<内容1> <内容2> ...)"
    "rand(<内容1> <内容2> ...)"


例文::

    "random(おはよう おはようございます Hello Hi Hey 'Good morning')"
