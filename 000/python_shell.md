.. _Using Python shell:

Pythonシェルを使う
==================

.. contents::
  :local:

Pythonインタラクティブシェル
----------------------------

:command:`python` コマンドはCUI（コマンドライン・ユーザ・インターフェイス）の対話式シェルです。
どういうものか、まず使ってみましょう。

shellプロンプトに次のように打ちます。

.. highlight:: sh

::

  $ python

すると、次のような表示になります。

.. highlight:: pycon

::

  Python 2.7.2 (default, Oct 11 2012, 20:14:37)
  [GCC 4.2.1 Compatible Apple Clang 4.0 (tags/Apple/clang-418.0.60)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>> 

Pythonインタラクティブシェルが起動した状態です。
1行目は、Pythonのバージョンが表示されています。
2行目は、Pythonのビルド情報です。
3行目は、"help"などを入力することで追加情報を得られることが表示されてます。
4行目は、Pythonインタラクティブシェルの標準プロンプトです。

Pythonインタラクティブシェルを終了して、元のshellに戻るには :kbd:`Control-D` （controlキーを押しながらDキーを押す）を入力します。

::

  >>> Control-D
  $

.. _iPython intaractive shell:

iPythonインタラクティブシェル
-----------------------------

高機能なPythonインタラクティブシェルのiPythonを使用していきます。
簡単な操作でより高度な情報を得られるので、通常はiPythonを使います。

.. highlight:: sh

.. note::

  iPythonを現在の仮想環境にインストールしておいてください。

  ::

    (iPython)$ pip install ipython
    (iPython)$ pip freeze
    ...
    ipython==1.1.0
    ...
    (iPython)$ which ipython
    $HOME/.virtualenvs/iPython/bin/ipython

iPythonを起動するには、shellプロンプトに次のように打ちます。

::

  (iPython)$ ipython

すると、次のような表示になります。

.. highlight:: pycon

::

  Using Virtualenv => $HOME/.virtualenvs/iPython/lib/python2.7/site-packages
  Python 2.7.2 (default, Oct 11 2012, 20:14:37) 
  Type "copyright", "credits" or "license" for more information.

  IPython 1.1.0 -- An enhanced Interactive Python.
  ?         -> Introduction and overview of IPython's features.
  %quickref -> Quick reference.
  help      -> Python's own help system.
  object?   -> Details about 'object', use 'object??' for extra details.

  In [1]: 

1行目は、Python仮想環境を使用している旨が表示されています。
2行目は、Pythonのバージョンが表示されています。
3行目は、追加情報を得られることが表示されてます。

5行目は、iPythonのバージョンが表示されています。
6行目から9行目は、iPythonの追加情報を得られることが表示されています。

11行目は、iPythonインタラクティブシェルの標準プロンプトが表示されています。

iPythonインタラクティブシェルを終了して、元のshellに戻るには :kbd:`Control-D` （controlキーを押しながらDキーを押す）を入力します。

::

  In [1]: Control-D
  Do you really want to exit ([y]/n)? 

すると、終了を確認するメッセージが表示されるので `y` を入力します。

::

  In [1]: Control-D
  Do you really want to exit ([y]/n)? y
  (iPython)$

.. note::

  iPythonインタラクティブシェルのプロンプトを、Pythonインタラクティブシェル標準プロンプトと同じ表示に変更するには、
  `%doctest_mode` を入力します。

  ::

    In [1]: %doctest_mode
    Exception reporting mode: Plain
    Doctest mode is: ON
    >>> 

  または、次のオプションを指定してiPythonを起動します。

  ::

    (iPython)$ ipython -c "%doctest_mode" -i
    ...
    Exception reporting mode: Plain
    Doctest mode is: ON
    >>> 

.. _Using iPython:

iPythonを使う
-------------

それでは、iPythonインタラクティブシェルを使ってみます。
便利な操作について学びます。

"import " （"import"の文字列に続けて半角スペース）を入力してから :kbd:`tab` キーを入力します。

::

  >>> import 
  Audio_mac       _CG         _hashlib  base64          doctest       importlib   pdb           sched       this
  BaseHTTPServer  _CarbonEvt  _heapq    bdb             docutils      imputil     pickle        select      thread
  Bastion         _Cm         _hotshot  bgenlocations   dumbdbm       inspect     pickletools   sets        threading
  CGIHTTPServer   _Ctl        _io       binascii        dummy_thread  io          pimp          setuptools  time
  ...
  >>> import 

すると、import可能なモジュールの一覧が表示されます。

さらに "r" の文字を入力してから :kbd:`tab` キーを入力します。

::

  >>> import r
  random      repr        rfc822        robotparser   rst2man             rst2pseudoxml   rst2xml
  re          resource    rlcompleter   rst2html      rst2odt             rst2s5          rstpep2html
  readline    rexec       rmagic        rst2latex     rst2odt_prepstyles  rst2xetex       runpy
  >>> import r

すると、"r"から始まるモジュールに絞られて表示されます。

さらに、"import ra"までを入力してから :kbd:`tab` キーを入力します。

::

  >>> import ra

すると、"import random"までが自動的に補完されます。

::

  >>> import random

続いて :kbd:`return` キーを入力してします。

何表示が変わりませんが、randomモジュールが読み込まれました。
"random"を入力すると、randomモジュールオブジェクトが表示されます。

::

  >>> random
  <module 'random' from '/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/random.pyc'>

次に "random."を入力してから :kbd:`tab` キーを入力します。

::

  >>> random.
  random.BPF            random.Random         random.WichmannHill  random.expovariate   random.getstate        random.paretovariate  random.sample    random.triangular
  random.LOG4           random.SG_MAGICCONST  random.betavariate   random.gammavariate  random.jumpahead       random.randint        random.seed      random.uniform
  random.NV_MAGICCONST  random.SystemRandom   random.choice        random.gauss         random.lognormvariate  random.random         random.setstate  random.vonmisesvariate
  random.RECIP_BPF      random.TWOPI          random.division      random.getrandbits   random.normalvariate   random.randrange      random.shuffle   random.weibullvariate

すると、randomモジュールオブジェクトの属性が表示されます。

"random.random" を入力してから :kbd:`return` キーを押下すると、randomモジュールオブジェクトのrandom属性を表示します。

::

  >>> random.random
  <built-in method random of Random object at 0x7fdad090bc20>

"method"とは呼び出し可能な属性です。
"random.random()"を入力してから :kbd:`return` キーを押下し、属性を呼び出します。

::

  >>> random.random()
  0.9144904558091682

属性名から察するにランダムな値を返していると推測できますが、"random.random"が一体なになのか確認するには、
"random.random?"を入力してから :kbd:`return` キーを押下します。

::

  >>> random.random?
  Type:       builtin_function_or_method
  String Form:<built-in method random of Random object at 0x7fdad090bc20>
  Docstring:  random() -> x in the interval [0, 1).

簡単な仕様が表示されます。

ここで、 "_"を入力しから :kbd:`return` キーを押下してみましょう。

::

  >>> _
  0.9144904558091682

"_"には、直前に実行した結果が保存されていますので、有効に使うとよいでしょう。

::

  >>> value = _
  >>> value == random.random()
  False

.. note::

  Pythonオブジェクトを更に詳しく調べたいときには、調べたい対象の後に"??"を入力してから :kbd:`return` キーを押下し、ソースコードを確認することができます。

  ※"random.random"はビルトインオブジェクト（C言語で書かれたオブジェクト）なので、これ以上の情報は表示されません。

  ::

    >>> import asyncore
    >>> asyncore.socket??
    Type:       module
    String Form:<module 'socket' from '/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/socket.pyc'>
    File:       /System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/socket.py
    Source:
    # Wrapper module for _socket, providing some additional facilities
    # implemented in Python.

    """\
    This module provides socket operations and some related functions.
    On Unix, it supports IP (Internet Protocol) and Unix domain sockets.
    On other systems, it only supports IP. Functions specific for a
    socket are available as methods of the socket object.

    Functions:

    socket() -- create a new socket object
    socketpair() -- create a pair of new socket objects [*]
    fromfd() -- create a socket object from an open file descriptor [*]
    gethostname() -- return the current hostname
    gethostbyname() -- map a hostname to its IP number
    gethostbyaddr() -- map an IP number or hostname to DNS info
    getservbyname() -- map a service name and a protocol name to a port number
    getprotobyname() -- map a protocol name (e.g. 'tcp') to a number
    ntohs(), ntohl() -- convert 16, 32 bit int from network to host byte order
    htons(), htonl() -- convert 16, 32 bit int from host to network byte order
    inet_aton() -- convert IP addr string (123.45.67.89) to 32-bit packed format
    inet_ntoa() -- convert 32-bit packed format IP to string (123.45.67.89)
    ssl() -- secure socket layer support (only available if configured)
    socket.getdefaulttimeout() -- get the default timeout value
    socket.setdefaulttimeout() -- set the default timeout value
    create_connection() -- connects to an address, with an optional timeout and
                           optional source address.

     [*] not available on all platforms!
    ...
