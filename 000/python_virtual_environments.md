.. _`Using the Python virtual environments`:

Python仮想環境を使う
====================

.. note:: :doc:`setup_Python_virtual_environments`

これらのコマンドについて使い方を学びます。

.. highlight:: sh

使用例:

- :command:`mkvirtualenv`::

  $ mkvirtualenv ENV_NAME

- :command:`rmvirtualenv`::

  $ rmvirtualenv ENV_NAME

- :command:`workon`::

  $ workon
  $ workon ENV_NAME

- :command:`deactivate`::

  $ deactivate

- :command:`pip`::

  $ pip freeze
  $ pip search QUERY
  $ pip install PACKAGE_NAMES
  $ pip uninstall PACKAGE_NAMES

例として、iPyhton Notebook用に新しいPython仮想環境 `notebook` を作成する手順です。

.. contents::
   :local:

Python仮想環境を作成する
------------------------

:command:`mkvirtualenv` コマンドで、新しいPython仮想環境を作成します。
第1引数に新しいPython仮想環境の名前を指定します。
ここでは `notebook` を指定します。

::

  $ mkvirtualenv notebook
  ...
  (notebook)$

コマンドラインプロンプトに `(notebook)` が表示されるようになりました。
現在のPython仮想環境の名前を表示しています。
現在のPython仮想環境を確認するには、コマンドラインプロンプトの表示を確認します。

現在のPython仮想環境の状態を確認する
------------------------------------

:command:`pip freeze` コマンドは、現在のPython環境にインストールされているPythonライブラリの一覧を表示します。

::

  (notebook)$ pip freeze
  wsgiref==0.1.2

.. note::

  :command:`pip` は環境変数 `PIP_RESPECT_VIRTUALENV` によってPython仮想環境上で動作するように設定しています。

  :download:`dotfiles/.zshrc.python`::

    export PIP_RESPECT_VIRTUALENV=true

Python仮想環境へPythonライブラリをインストールする
--------------------------------------------------

:command:`pip install` コマンドは、現在のPython環境にPythonライブラリをインストールします。

::

  (notebook)$ pip install ipython
  ...
    Installing ipython script to $HOME/.virtualenvs/notebook/bin
  ...
  Successfully installed ipython
  Cleaning up...

インストールが終了すると :command:`ipython` コマンドへPATHが通っていることが確認できます。

::

  (notebook)$ which ipython
  $HOME/.virtualenvs/notebook/bin/ipython

.. todo::
  File "/Users/endoh/.ipython/profile_default/ipython_config.py", line 385, in <module>
    from commands import getoutput
  ImportError: No module named 'commands'

  ******************************************************************************
  libedit detected - readline will not be well behaved, including but not limited to:
     * crashes on tab completion
     * incorrect history navigation
     * corrupting long-lines
     * failure to wrap or indent lines properly
  It is highly recommended that you install readline, which is easy_installable:
       easy_install readline
  Note that `pip install readline` generally DOES NOT WORK, because
  it installs to site-packages, which come *after* lib-dynload in sys.path,
  where readline is located.  It must be `easy_install readline`, or to a custom
  location on your PYTHONPATH (even --user comes after lib-dyload).
  ******************************************************************************

.. note::

  Python 3.xの環境では :command:`ipython3` です。

::

  (notebook)$ which ipython3
  $HOME/.virtualenvs/notebook/python3.3/bin/ipython3


.. note::

  Pythonで最もよく遭遇するエラー: ImportError

  ここで iPython Notebook を起動してみます。
  :command:`ipython notebook` コマンドを実行します。

  ::

    $ ipython notebook
    ...
    ImportError: The IPython notebook requires tornado >= 2.1.0

  なにやら "Error" の文字が表示されて何も起こりませんが、慌てないでください。
  きちんと必要なメッセージが表示されているので、よく *見て* みましょう。
  表示されたメッセージをよく見て、内容を *理解* することが最も重要です。
  Pythonにおいては、最終行に表示されているメッセージが特に重要なので、書き留めておくなりして紛失しないようにしましょう。

  "ImportError" は "import error" です。日本語に訳すると "インポート エラー" です。
  Pythonプログラム内で外部のPythonモジュールを読み込もうとした際に、何らかの原因で失敗すると送出される例外です。

  "ImportError:" に続く文字列は、例外を送出した原因に関するメッセージです。
  "The IPython notebook requires tornado >= 2.1.0" とは "IPython notebook は tornado 2.1.0+ を必要としている" という意味です。

  このエラーを回避する方法は `tornado 2.1.0+` をインストールすることです。

  .. note::

    Pythonは国際的に利用されているプログラミング言語なので、重要なメッセージは事実上の業界標準言語である英語で表示されます。

.. note::

  :command:`pip search` コマンドで、オンラインで配布されているPythonライブラリを検索できます。

  ::

    $ pip search ipython
    ipython                   - IPython: Productive Interactive Computing
    ipython-cluster-helper    - Simplify IPython cluster start up and use for multiple schedulers.
    ipdb                      - IPython-enabled pdb
    ipython-sql               - RDBMS access via IPython
    ...

:command:`ipython notebook` の実行に必要な、残りのPythonライブラリをインストールします。
必要なライブラリの一覧は :download:`requirements/iPython-Notebook.txt` に用意してあるので、これを利用します。

:download:`requirements/iPython-Notebook.txt`:

.. literalinclude:: requirements/iPython-Notebook.txt
  :language: ini

:command:`pip install` コマンドの `-r` オプションで requirements ファイルの一覧をインストールします。

::

  (notebook)$ pip install -r requirements/iPython-Notebook.txt
  ...

:command:`ipython notebook` コマンドを実行すると iPython Notebook サーバが起動し、 iPython Notebook のダッシュボードがWebブラウザで開きます。

::

  (notebook)$ ipython notebook
  ...
  2013-12-11 10:04:38.977 [notebookApp] The IPython notebook is running at: http://127.0.0.1:8888/
  ...

iPython Notebook を終了するには :command:`ipython notebook` コマンドを実行したコンソールで :kbd:`Control-C` を押下します。
（ `control` キーを押下したまま `C` キーを押下する ）

::

  ...
  Shutdown this notebook server (y/[n])?

すると、確認のメッセージが表示されるので `y` を入力して :kbd:`return` キーを押下すると、終了してプロンプトに戻ります。

::

  ...
  Shutdown this notebook server (y/[n])? y
  2013-12-13 14:05:02.537 [NotebookApp] CRITICAL | Shutdown confirmed
  2013-12-13 14:05:02.539 [NotebookApp] Shutting down kernels
  (notebook)$

iPython Notebook ダッシュボードが表示されているWebブラウザは、閉じて構いません。

Python仮想環境から抜ける
------------------------

:command:`deactivate` コマンドで、Python仮想環境を抜けます。

::

  (notebook)$ deactivate
  $

コマンドラインプロンプトに表示されていた、Python仮想環境の名前 `(notebook)` の表示が消えました。

Python仮想環境に入る
--------------------

:command:`workon` コマンドは、既存のPython仮想環境の一覧を表示します。

::

  $ workon
  appengine
  notebook
  pypy
  python2.6
  python2.7
  python3.2
  python3.3
  python3.4
  test
  ...

:command:`workon` コマンドでPython仮想環境の名前を指定し、既存のPython仮想環境に入ります。

::

  $ workon notebook
  (notebook)$

Python仮想環境を削除する
------------------------

:command:`rmvirtualenv` コマンドでPython仮想環境の名前を指定して削除します。

::

  $ rmvirtualenv notebook
  Removing notebook...

.. note::

  削除しようとしているPython仮想環境を使用している状態では、削除できません。

  ::

    (notebook)$ rmvirtualenv notebook
    Removing notebook...
    ERROR: You cannot remove the active environment ('notebook').
    Either switch to another environment, or run 'deactivate'.

  :command:`deactivate` コマンドで、削除しようとしているPython仮想環境を抜けてから、削除を実行します。

  ::

    (notebook)$ deactivate
    $ rmvirtualenv notebook
    Removing notebook...

