.. _testing:

======================
Tests for Page Objects
======================

``web-poet`` provides :ref:`tools for testing page objects
<web-poet:web-poet-testing>`. ``scrapy-poet`` projects can use a Scrapy command
to easily generate tests::

    scrapy savefixture my_project.pages.MyItemPage 'https://quotes.toscrape.com/page/1/'

This will request the provided page, create an instance of the provided page
object for this page, request its :meth:`~web_poet.pages.ItemPage.to_item`
method and save both the page object dependencies and the resulting item as a
test fixture. These fixtures can then be used with the ``pytest`` plugin
provided by ``web-poet``.

Configuring the test location
=============================

The ``SCRAPY_POET_TESTS_DIR`` setting specifies where to create the tests. It
can be set in the project settings or with the ``-s`` command argument.

Handling time fields
====================

The tests generated by ``savefixture`` set the :ref:`frozen_time metadata value
<web-poet:web-poet-testing-frozen_time>` to the time of the test creation.
