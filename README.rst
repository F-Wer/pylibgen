pylibgen
==========================
|License MIT|


Python interface to Library Genesis.

Currently supports the :code:`libgen.io` mirror. Will need to write custom parsers for other mirrors in the future.

**This is fork of [pylibgen](https://github.com/JoshuaRLi/pylibgen) meant to work with python 2.7 without any external dependecnies (like requests)**

Usage
---------------------

.. code-block:: pycon

    >>> from pylibgen import Library
    >>> lg = Library()
    >>> ids = lg.search('automate the boring stuff', 'title')
    >>> ids

    ['1421206', '1421207', '1421208', '1351717', '1381538', '1381540', '1529338']
    
    >>> books = lg.lookup(ids)
    >>> from pprint import pprint; pprint(books[0])

    {'author': 'Albert Sweigart',
     'edition': '',
     'extension': 'epub',
     'filesize': '4485769',
     'identifier': '978-1593275990',
     'md5': '054255117b2e86251415292ef48320fd',
     'pages': '0',
     'title': 'Automate the Boring Stuff with Python: Practical Programming for '
              'Total Beginners',
     'year': '2015'}

    >>> lg.get_download_url(books[0]['md5'])

    'http://libgen.io/get.php?md5=054255117b2e86251415292ef48320fd&key=NQTP585IPY102LYG'

Compatibility
---------------------

pylibgen is tested to work with python 3.3 - 3.6.

Notes
---------------------

Due to the nature of the service Library Genesis provides, its mirrors often get taken down. Feel free to submit any pull requests to update :code:`constants.MIRRORS` as time goes on!

Support Library Genesis!
--------------------------

:code:`Library.get_download_url` will by default parse the temporary download key from libgen's ads.php redirect page. This is necessary for a valid direct download URL since libgen uses those temp keys to get more ad revenue.

If you want to support Library Genesis, I recommend passing :code:`enable_ads=True` to :code:`Library.get_download_url`. This will return the plain download URL, which shows an ad first when visited.

Disclaimer
---------------------

Use this at your own risk. I am not responsible or liable for any piracy, copyright infringement, or other things committed by anyone using pylibgen. Blah blah lawyer stuff, etc.
