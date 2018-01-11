.. Licensed to the Apache Software Foundation (ASF) under one
.. or more contributor license agreements.  See the NOTICE file
.. distributed with this work for additional information
.. regarding copyright ownership.  The ASF licenses this file
.. to you under the Apache License, Version 2.0 (the
.. "License"); you may not use this file except in compliance
.. with the License.  You may obtain a copy of the License at
..
..     http://www.apache.org/licenses/LICENSE-2.0
..
.. Unless required by applicable law or agreed to in writing, software
.. distributed under the License is distributed on an "AS IS" BASIS,
.. WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
.. See the License for the specific language governing permissions and
.. limitations under the License.


Working on Documentation
*************************

How Cassandra is documented
===========================

The official Cassandra documentation lives in the project's git repository. We use a static site generator, `Sphinx <http://www.sphinx-doc.org/>`_, to create pages hosted at `cassandra.apache.org <https://cassandra.apache.org/doc/latest/>`_. You'll also find developer centric content about Cassandra internals in our retired `wiki <https://wiki.apache.org/cassandra>`_ (not covered by this guide).

Using a static site generator often requires to use a markup language instead of visual editors (which some people would call good news). Sphinx, the tool-set we use to generate our documentation, uses `reStructuredText <http://www.sphinx-doc.org/en/stable/rest.html>`_ for that. Markup languages allow you to format text by making use of certain syntax elements. Your document structure will also have to follow specific conventions. Feel free to take a look at `existing documents <..>`_ to get a better idea how we use reStructuredText to write our documents.

So how do you actually start making contributions?

GitHub based work flow
======================

*Recommended for shorter documents and minor changes on existing content (e.g. fixing typos or updating descriptions)*

Follow these steps to contribute using GitHub. It's assumed that you're logged in with an existing account.

1. Fork the GitHub mirror of the `Cassandra repository <https://github.com/apache/cassandra>`_

.. image:: images/docs_fork.png

2. Create a new branch that you can use to make your edits. It's recommended to have a separate branch for each of your working projects. It will also make it easier to create a pull request later to when you decide you’re ready to contribute your work.

.. image:: images/docs_create_branch.png

3. Navigate to document sources ``doc/source`` to find the ``.rst`` file to edit. The URL of the document should correspond  to the directory structure. New files can be created using the "Create new file" button:

.. image:: images/docs_create_file.png

4. At this point you should be able to edit the file using the GitHub web editor. Start by naming your file and add some content. Have a look at other existing ``.rst`` files to get a better idea what format elements to use.

.. image:: images/docs_editor.png

Make sure to preview added content before committing any changes.

.. image:: images/docs_preview.png

5. Commit your work when you're done. Make sure to add a short description of all your edits since the last time you committed before.

.. image:: images/docs_commit.png

6. Finally if you decide that you're done working on your branch, it's time to create a pull request!

.. image:: images/docs_pr.png

Afterwards the GitHub Cassandra mirror will list your pull request and you're done. Congratulations! Please give us some time to look at your suggested changes before we get back to you.


Jira based work flow
====================

*Recommended for major changes*

Significant changes to the documentation are best managed through our Jira issue tracker. Please follow the same `contribution guides <https://cassandra.apache.org/doc/latest/development/patches.html>`_ as for regular code contributions. Creating high quality content takes a lot of effort. It’s therefor always a good idea to create a ticket before you start and explain what you’re planing to do. This will create the opportunity for other contributors and committers to comment on your ideas and work so far. Eventually your patch gets a formal review before it is committed.

Working on documents locally using Sphinx
=========================================

*Recommended for advanced editing*

Using the GitHub web interface should allow you to use most common layout elements 
including images. More advanced formatting options and navigation elements depend on
Sphinx to render correctly. Therefore it is a good idea to setup Sphinx locally for any 
serious editing. 
Since a setup under windows isn't easily possible, it is recommended to
use OSX or Linux for any work with Sphinx. 
Furthermore ensure that you have a python version on your OS. After some struggles appeared
with version 3.0 , it is helpful to use version 2.7.

You can install sphinx with the pip command as the following:: 


	pip install sphinx_rdt_theme 

Now you should be able to build the documentation.
So change to the doc diretory in your cassandra fork. And use::

	 make html

You will find the created html files in your cassandra directory under doc/build/html/...

More instructions for installing sphinx and build the documentation, you can find 
at ``doc/README.md`` .


Short texthighlight instructions for using Sphinx
=================================================

For a fast start, here are some commands:

Create a title:: 
	
	How to make a title
	===================

Make a box for commands::

	With two colons at the end you create a box for example commands::

Example : With two colons at the end you create a box for example commands::

	pip...

Write a cursive text:: 

	*cursive font*

*cursive font*

Highlight something with red font color:: 
	
	``doc/README.md``

``doc/README.md``

Insert an image:: 

	.. image:: images/example.png

use a hyperlink:: 

	`Sphinx <http://www.sphinx-doc.org/>`_

`This <http://www.sphinx-doc.org/>`_  is the link to the official Sphinx Homepage, where you are able to look up more information for sphinx and the editing style.

Notes for committers
====================

Please feel free to get involved and merge pull requests created on the GitHub mirror if you're a committer. As this is a read-only repository,  you won't be able to merge a PR directly on GitHub. You'll have to commit the changes against the Apache repository with a comment that will close the PR when the committ syncs with GitHub.

You may use a git work flow like this::

   git remote add github https://github.com/apache/cassandra.git
   git fetch github pull/<PR-ID>/head:<PR-ID>
   git checkout <PR-ID>

Now either rebase or squash the commit, e.g. for squashing::

   git reset --soft origin/trunk
   git commit --author <PR Author>

Make sure to add a proper commit message including a "Closes #<PR-ID>" text to automatically close the PR.

Publishing
----------

Details for building and publishing of the site at cassandra.apache.org can be found `here <https://svn.apache.org/repos/asf/cassandra/site/src/README>`_.
