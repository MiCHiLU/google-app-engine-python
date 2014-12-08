Python仮想環境を設定する
========================

Set up the Python virtual environments

Python仮想環境は、次のツールを利用して構築します。

- Setuptools 2.0+ (not Setuptools 1.x or Distribute)
- pip
- virtualenv
- virtualenvwrapper

.. contents::
   :local:

Installing Setuptools 2.0+
--------------------------

.. highlight:: sh

古いバージョンの Setuptools または Distribute をインストールしている環境では、アップグレードの作業が必要です。
https://pypi.python.org/pypi/setuptools#installation-instructions

手っ取り早い方法としては、 現在のシステムの Setuptools と Distribute パッケージファイルをすべて削除します。

::

  $ sudo rm -rf /Library/Python/**/(distribute|setuptools)*
  $ sudo rm -rf /Library/Frameworks/Python.framework/**/(distribute|setuptools)*
  $ sudo rm /usr/bin/easy_install*

すべて削除できたか確認して下さい。

::

  $ ls /Library/Python/**/(distribute|setuptools)*
  zsh: no matches found: /Library/Python/**/(distribute|setuptools)*
  $ ls /Library/Frameworks/Python.framework/**/(distribute|setuptools)*
  zsh: no matches found: /Library/Frameworks/Python.framework/**/(distribute|setuptools)*
  $ ls /usr/bin/easy_install*
  zsh: no matches found: /usr/bin/easy_install*

クリーンな状態になったら、 Setuptools 2.0+ をシステムワイドへインストールします。

::

  $ curl -s https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py | sudo python
  $ curl -s https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py | sudo python3

Setuptoolsをインストールすると :command:`easy_install` が使えるようになります。

Installing pip
--------------

:command:`easy_install` で pip をシステムワイドへインストールします。

::

  $ sudo easy_install pip

Installing virtualenv
---------------------

:command:`pip` で virtualenv をシステムワイドへインストールします。

::

  $ sudo pip install --upgrade virtualenv

.. note::

  :command:`pip` コマンドの `--update` オプションは指定すると、最新のバージョンをインストールします。

.. todo::

  pip3を併記する

Installing virtualenvwrapper
----------------------------

:command:`pip` で virtualenvwrapper をシステムワイドへインストールします。

::

  $ sudo pip install --upgrade virtualenvwrapper

環境変数を設定する
------------------

次の内容を :file:`$HOME/.zshrc` へ追記し、 :command:`zsh` を再起動します。

.. literalinclude:: dotfiles/.zshrc.python
  :language: sh
  :linenos:
  :lines: 1-19
