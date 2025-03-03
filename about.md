---
layout: page
title: About
permalink: /about/
---

## LinguaPhylo (LPhy for short - pronounced el-fee)

LinguaPhylo (LPhy for short - pronounced el-fee) is a probabilistic model specification language to concisely and precisely define phylogenetic models.
The aim is to provide a language (work towards a _lingua franca_) for probabilistic models of phylogenetic evolution that is independent of the method to perform inference.
This language is readable by both humans and computers. Here is a full example:

{::nomarkdown}
{% include_relative yule.html %}
{:/}

Each of the lines in this model block expresses how a random variable (to the left of the tilde) is generated from a generative distribution.

The first line creates a random variable, λ, that is log-normally distributed.
The second line creates a tree, ψ, with 16 taxa from the Yule process with a lineage birth rate equal to λ.
The third line produces a multiple sequence alignment with a length of 200, by simulating a Jukes Cantor model of sequence evolution down the branchs of the tree ψ.
As you can see, each of the random variables depends on the last, so this is a hierarchical model that ultimately defines a probability distribution of sequence alignments of size 16 x 200.

LinguaPhylo is an open source project. 
The source is hosted at [https://github.com/LinguaPhylo/linguaPhylo](https://github.com/LinguaPhylo/linguaPhylo).

### LinguaPhylo Studio

Along with the language definition, we also provide software to specify and visualise models as well as simulate data from models defined in LPhy.

This software will also provide the ability for models specified in the LPhy language to be applied to data using standard inference tools such as MrBayes, RevBayes, BEAST1 and BEAST2.
This will require software that can convert an LPhy specification into an input file that these inference engines understand.
The first such software converter is LPhyBEAST described below.

## LPhyBEAST (pronounced el-fee-beast)

[LPhyBEAST](https://github.com/LinguaPhylo/LPhyBeast) is a command-line program that takes an LPhy model specification, and some data and produces a BEAST 2 XML input file.
It is therefore an alternative way to succinctly express and communicate BEAST analyses.
