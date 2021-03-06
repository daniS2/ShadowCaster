.. ShadowCaster documentation master file, created by
   sphinx-quickstart on Sun Jul 29 22:36:06 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

ShadowCaster's documentation
============================

ShadowCaster implements an evolutionary model to calculate Bayesian likelihoods for each 'alien genes' with an unusual sequence composition according to the host genome background to detect HGT events in prokaryotes. 


ShadowCaster analysis workflow
-------------------------------
1. The user defines a query genome (by providing two fasta files, see :doc:`usage` ) in which HGT events will be detected. 
2. ShadowCaster uses a list of proteomes from phylogenetically related species to the query genome (one proteome FASTA file per species) to construct a phylogenetic shadow.

  The list of proteomes could be either:
   -Provided by the user (a collection of FASTA files).
   
   -Automatically retrieved by ShadowCaster from the NCBI ftp site by using ``script/get_proteomes.py``, see :doc:`scripts`.
    
3. A prioritized list of potential 'alien genes' present in the query genome is generated by the analysis of compositional features i.e. 4mers and codon usage. An unsupervised one-class support vector machine is used for the prioritization task. 

4. Orthology relationships among the query genome and its phylogenetically related species are obtained by the third-party algorithm ORTHOMCL. This information is used to calculate the 'probability of orthology' between the query genome and each other genome in the phylogenetic shadow. 

5. BLAST is used to calculate the identity between each alien gene and the rest of genes in the genomes of the phylogenetic shadow. 

6. A likelihood is calculated for each alien genes in the list from step 3. The likelihood expresses how likely is that the pattern of identity across genomes in the phylogenetic shadow for this alien gene derives from vertical inheritance.  


Installation
------------

For a comprehensive guide on how to install ShadowCaster and its prerequisites, see :doc:`installation`.


Contribute
----------
- Issue Tracker:  `issues <https://github.com/dani2s/ShadowCaster/issues>`_
- Source Code: `code <https://github.com/dani2s/ShadowCaster>`_



Support
-------

Send additional enquiries to asanchez2@utpl.edu.ec


License
-------

GNU General Public License Version 3


Contents
========

.. toctree::
   :maxdepth: 2
   
   self
   installation
   usage
   example
   scripts

