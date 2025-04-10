Homer
#####


.. image:: https://img.shields.io/badge/Made%20with-Python-1f425f.svg
   :target: https://www.python.org/
   :alt: Made with Python

.. image:: https://img.shields.io/pypi/pyversions/homer-text
   :target: https://pypi.org/project/homer-text/
   :alt: Python versions

.. image:: https://img.shields.io/pypi/l/homer-text
   :target: https://pypi.org/project/homer-text/
   :alt: Pypi licence

.. image:: https://img.shields.io/github/issues-raw/wyounas/homer
   :target: https://github.com/wyounas/homer/issues
   :alt: Issues


.. contents::

.. section-numbering::




Homer is a Python package that can help make your text more clear, simple and useful for the reader.
It provides information on an overall text as well as on individual paragraphs. It gives insights into readability, length of paragraphs, length of sentences, average sentences per paragraph, average words in a sentence, etc. It also tries to identify certain kind of vague words. It also tracks the frequency of "and" words in the text. (More information on all of these follows in the `Acknowledgements` section.)

This software package grew out of a personal need. Since I am not a native English speaker but am interested in writing, I designed and have been using Homer to improve my writing. I hope others will find it useful.

Please note that this is not a strict guide to control your writing. At least, I don't use it that way. I use it as a guide to make my writing as simple as possible. I strive to write concise paragraphs and sentences as well as use fewer unclear words, and Homer has been helping me.

I have only used it to analyze my blogs and essays and not the large corpus of text. As this software is new, you may well spot bugs, in which case please feel free to open up issues/pull-requests.

You can use Homer as a stand-alone package or on the command line. If you run it on the command line, you can get general stats on your article or essay as well as paragraph stats.

Features
========

Article/Essay Stats
-------------------

Running Homer from the command line gives the following insights about the article/essay:

* Reading time in minutes (although this will vary some from reader to reader).
* Readability scores (Flesch reading ease and Dale Chall readability scores).
* Total paragraphs, sentences, and words.
* Average sentences per paragraph.
* Average words per sentence.
* "and" frequency.
* Number and list of compulsive hedgers, intensifiers, vague words.


.. class:: no-web

    .. image:: https://drive.google.com/uc?export=view&id=19E7MDoMObkwGrN2FceXv9qjZLzBLBg6U
        :alt: overall stats
        :width: 100%
        :align: center


Paragraph Stats
---------------

Paragraph stats point out the following information for each paragraph:

* Number of sentences and words.
* Average words per sentence.
* The longest sentence in the paragraph.
* Readability scores (Flesch reading ease and Dale Chall readability scores).
* If the number of sentences is more than five in a paragraph, then Homer gives a warning highlighted in red.
* Similarly, when the number of words is more than 25 in a sentence, then a warning highlighted in red is given.

.. class:: no-web

    .. image:: https://drive.google.com/uc?export=view&id=1tnXSEh7nWQrtO3glDbtsoD_N-Q-xt2-h
        :alt: paragraph stats
        :width: 100%
        :align: center


Installation
============

Python
------

I built this on Python 3.4.5. So first we need to install Python.

On Mac, I used Homebrew to install Python e.g. one can use this command:

.. code-block:: bash
    $ brew install python3


To install on Windows, you can download the installer from `here <https://www.python.org/downloads/windows/>`_. Once downloaded this installer can be run to complete Python's installation.

For Ubuntu you might find this `resource <https://askubuntu.com/questions/802279/how-to-install-python-3-4-5-from-apt>`_ useful.


Virtual environment
-------------------

Now it's time to create a virtual environment (assuming you cloned the code under `~/code/homer`).

.. code-block:: bash
    ~/code/homer $ python3 -m venv venv
    ~/code/homer $ source venv/bin/activate

First line in the above snippet creates a virtual environment named `venv` under `~/code/homer`. The second command activates the virtual environment.

In case you need more help with creating a virtual environment this `resource <https://docs.python.org/3/library/venv.html>`_ can prove to be useful.

Installing `Homer` via Pip
--------------------------

Install using Pip:

.. code-block:: bash

    ~/code/homer $ pip install homer-text


And that's it. It should install everything i.e. required libraries, NLTK packages and homer_text itself.


Usage
=====

First time
-----------
Prior to using it for the first time, make sure you have all `nltk` dictionary files:

.. code-block:: python

    import nltk
    nltk.download('punkt')
    nltk.download('cmudict')
    nltk.download('stopwords')


Command line
------------

A command line utility, under the `homer` directory, has been provided. Here is an example showing how to use it:

.. code-block:: bash

    > python homer_cmd.py --name article_name --author lalala --file_path=/correct/path/to/file.txt


Both `--name` and `--author` are optional whereas `file_path` is mandatory.

Code
====

You can also use Homer in your code. Here is an example:

.. code-block:: python

    # file: analyse.py
    import sys
    from homer.analyzer import Article
    from homer.cmdline_printer import ArticlePrinter

    article = Article('Article name', 'Author', open(sys.argv[1]).read())
    ap = ArticlePrinter(article)
    ap.print_article_stats()
    ap.print_paragraph_stats()

Use it like this:

.. code-block:: bash

    > python analyse.py text_to_analyse.md

Tests
=====

Tests can be run from the `tests` directory.


Users
=====

Homer is used in academia for research. It can be helpful to look at existing uses of Homer to learn how you can use it to design a robust
system for text analysis.

- **Babanejad, Nastaran, et al.** "The role of preprocessing for word representation learning in affective tasks."
  *IEEE Transactions on Affective Computing* 15.1 (2023): 254-272.

- **Campanile, Lelio, et al.** "On the Evaluation of BDD Requirements with Text-based Metrics: The ETCS-L3 Case Study."
  *Intelligent Decision Technologies: Proceedings of the 14th KES-IDT 2022 Conference.* Singapore: Springer Nature Singapore, 2022.

- **Dehaki, Nastaran Babanejad.** "Enriching Word Representation Learning for Affect Detection and Affect-Aware Recommendations." *PhD dissertation, York University, Toronto, Ontario* (2020).

If your work uses Homer, please send a PR to add it to this list!

Citation
========

If you use Homer in academic work, please cite the following:

.. code-block:: bibtex

    @misc{homer2019,
      author = {Waqas Younas},
      title = {Homer: A Thorough Text Analyzer.},
      year = {2019},
      howpublished = {\url{https://github.com/wyounas/homer}}
    }



Author & Contributors
=====================

Author:


* `Waqas Younas <http://wyounas.github.io>`_ (waqas.younas@gmail.com)

Contributors:


* https://github.com/voronaam
* https://github.com/fkarg


Acknowledgements
================

* Steven Pinker's `The Sense of Style: The Thinking Person's Guide to Writing in the 21st Century <https://www.amazon.com/Sense-Style-Thinking-Persons-Writing/dp/0143127799>`_. This book gave me quite a few insights. It also prompted me to include tracking of vague words, complex hedgers and intensifiers.

  - Complex hedgers: These are words such as _apparently, almost, fairly, nearly, partially, predominantly, presumably, rather, relative, seemingly, etc._

  - Intensifiers: Words such as _very, highly, extremely.

* Bankspeak:

    The Language of World Bank Reports, 1946–2012: https://litlab.stanford.edu/LiteraryLabPamphlet9.pdf. This source also gave me a few ideas. The idea to keep track of "and" and the vague words in a text was taken from here.

    -  "and" frequency: Basically it is the number of times the word "and" is used in the text (given as a percentage of total text). I try to keep it under 3 %.

    - Vague words is a list of words I compiled after reading the above report.  Using these words unnecessarily, or without giving them the proper context, can make a text more abstract. These are words such as _derivative, fair value, portfolio, evaluation, strategy, competitiveness, reform, growth, capacity, progress, stability, protection, access, sustainable, etc._


Contributing
============

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate. Also, add your name under `Authors` section of the `readme` file.


License
=======
`MIT <https://choosealicense.com/licenses/mit/>`_
