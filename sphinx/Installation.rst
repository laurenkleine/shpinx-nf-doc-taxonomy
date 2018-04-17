Installation Tutorial
=====================

.. role:: bash(code)
   :language: bash

Connect to remote server:

:bash:`$ ssh [USER]@[system]`

Install Nextflow:

:bash:`$ curl -s https://get.nextflow.io | bash`

Move Nextflow executable into your $PATH:

:bash:`$ mv nextflow $HOME/bin`

Make test directory:

:bash:`$ mkdir amr_test && cd amr_test`

Download pipeline source code:

:bash:`$ git clone https://github.com/laurenkleine/taxonomy-nf .`
