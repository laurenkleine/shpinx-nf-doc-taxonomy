Installation Tutorial
=====================

Connect to remote server:

$ ssh [USER]@[system]

Install Nextflow:

$ curl -s `https://get.nextflow.io` | bash

Move Nextflow executable into your $PATH:

$ mv nextflow $HOME/bin

Make test directory:

$ mkdir amr_test && cd amr_test

Download pipeline source code:

$ git clone `https://github.com/laurenkleine/taxonomy-nf` .
