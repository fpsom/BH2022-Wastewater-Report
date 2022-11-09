---
title: 'Exploring the landscape of the genomic wastewater surveillance ecosystem: a roadmap towards standardization'
title_short: 'Overview of the Genomic Wastewater Surveillance landscape'
tags:
  - Wastewater surveillance
authors:
  - name: Fotis Psomopoulos
    orcid: 0000-0002-8021-9162
    affiliation: 1
  - name: Ivan Topolsky
    orcid: 0000-0002-7561-0810
    affiliation: 2
  - name: Bérénice Batut
    orcid: 0000-0001-9852-1987
    affiliation: 3
affiliations:
  - name: Institute of Applied Biosciences, Centre for Research and Technology Hellas, Thessaloniki, Greece
    index: 1
  - name: Computational Biology Group, SIB Swiss Institute of Bioinformatics, Basel,Switzerland
    index: 2
  - name: University of Freiburg, Germany
    index: 3
date: 10 November 2022
cito-bibliography: paper.bib
event: ELIXIR BioHackathon 2022
biohackathon_name: "ELIXIR BioHackathon 2022"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Paris, France, 2022"
group: Wastewater Surveillance
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/fpsom/BH2022-Wastewater-Report
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Fotis Psomopoulos & Ivan Topolsky \emph{et al.}
---


<!--

The paper.md, bibtex and figure file can be found in this repo:

  https://github.com/journal-of-research-objects/Example-BioHackrXiv-Paper

To modify, please clone the repo. You can generate PDF of the paper by
pasting above link (or yours) in

  http://biohackrxiv.genenetwork.org/

-->

# Introduction

Nearly two years after the first report of SARS-CoV-2 in Wuhan, China, the COVID-19 pandemic has affected more than 485 million people. Wastewater surveillance has attracted extensive public attention during the SARS-CoV-2 pandemic, as a passive monitoring system to complement clinical and genomic surveillance activities. Several methods and protocols are already in place that effectively facilitate the detection and quantification of viral RNA in wastewater samples, and concentrations in wastewater have been shown to correlate with trends in reported cases.

With exploratory projects having shown promise, it is now important to coordinate among initiatives for establishing community standards and effectively building an inventory of the available software tools and services, in order to ultimately simplify the deployment of end-to-end genomic wastewater surveillance pipelines and increase the adoption of such promising monitoring methods across the wider community. The first step in this direction would be to identify and catalogue the relevant methodologies and bioinformatics workflows that are integral components of the lifecycle of genomic data derived from wastewater samples, combining into a coherent structure.

The main goal of this project has been to review, collate and offer a first attempt towards integrating, standardizing and reporting different approaches that are available for genomic wastewater surveillance. Leveraging the collective expertise of the [ELIXIR COVID19 Wastewater Surveillance Working Group](https://www.covid19dataportal.org/partners?activeTab=Working%20groups), we focussed on creating a comprehensive landscape of components (e.g. modules, tools etc) that can be effectively utilized for end-to-end genomic wastewater surveillance pipelines.

<!--
# Results
-->

# Defining the key elements of an omic Wastewater Surveillance framework

One of the first activities of the project was to review and identify the possible questions that an omic Wastewater Surveillance is expected to address, keeping in mind that a key requirement of the system is to produce actionable results, i.e. information that can be directly consumed by public health experts. For example, `VCF` files cannot be considered as actionable, as they require particular expertise to be understood; on the other hand, variant frequencies in a given sample are actionable, as they provide sufficient information to a public health expert to follow up.

An indicative list of these questions are:
1. Is virus `v` present in the wastewater sample?
  Essentially this is a question of presence/absence that is traditionally addressed through RT-PCR or equivalent methods. However, there are cases (such as the monkeypox virus) that RT-PCR cannot disambiguate easily, thus requiring a sequencing step to complement.

2. Is the variant `vv` present in the wastewater sample?

3. What is the longitudinal change of the variants?
  Essentially this is translated as identifying the trend of variant presence frequencies across multiple time points and samples.

4. What is the fitness advantage?
  This is one of the more advanced questions that could be addressed by wastewater surveillance, and involves the projection of the trajectory of a given variant in time and the calculation of a possible $R_e$.

5. What are potentially emerging variants?





# Standardizing definitions

Looking into viruses in particular, one of the main challenges is still the definition of variants. Of course, using public databases (i.e. public health registries and specialized repositories such as [outbreak.info](https://outbreak.info/)) is one of the approaches. However, given the multitude of potential variants and respective definitions, more often than not, tools use a custom list of pre-selected definitions (or even simplified versions of the same definitions). However, this approach implies that there is always going to be a human factor in the process, assessing which definitions (or parts of definitions) will be used.

In either case, it is important to identify what would be the minimal information expected as input to a federated omics wastewater surveillance system, i.e. reaching a consensus on how to tackle common definitions (looking also at FAIR definitions.)


Definition: Antimicrobial Resistance


Definition: Virulence factor




# Phases of Omic Wastewater Surveillance

We identify two main types of omic Wastewater Surveillance workflows;
- specific target (e.g. single virus and variants), usually amplicon based, and
-  unknown target metagenomics / metatranscriptomics

For each of these workflows, we have identified the key phases involved (not including the sampling and wet-lab parts of the process).

## Specific target (amplicon-based) workflow

Omics WW Surveillance System - specific target (e.g. single virus + variants) / amplicon based

- **Step 0**: RT-PCR
  _Objectives_: Rough presence/absence of virus. Plus variants depending on probe.
  _Actionable_: Yes (basic)
- **Step 1**: Sequencing
  _Objectives_: `FASTQ`/`FAST5` files - no further information.
  _Actionable_: No
- **Step 2**: Alignment to reference (incl. host removal + cleaning)
  _Objectives_: `BAM` file.
  _Actionable_: No
- **Step 3**: Identify mutations
  _Objectives_: `VCF` files, list of mutations, pileups, etc
  _Actionable_: No
- **Step 4**: Detect variants based on definitions
  _Objectives_: List of variants
  _Actionable_: Yes (variant level)
- **Step 5**: Quantify variants based on definitions
  _Objectives_: List of variants with frequencies (should add up to 100% per sample)
  _Actionable_: Yes (variant trends)
- **Step 6**: Define new variants based on mutations
  _Objectives_: List of mutations not mapping to known definitions
  _Actionable_: Yes (emerging variants)


## unknown target metagenomics / metatranscriptomics workflow

Omics WW Surveillance System - unknown target metagenomics/metatranscriptomics (depending on the type of target you are looking for)

- **Step 0**: RT-PCR
  _Objectives_: **Not possible/Not applicable**
  _Actionable_: No
- **Step 1**: Sequencing
  _Objectives_: `FASTQ`/`FAST5` files - no further information.
  _Actionable_: No
- **Step 2**: QC on reads (remove host sequencing)
  _Objectives_: `FASTQ`/`FAST5` files - no further information.
  _Actionable_: No
- **Step 3a**: Alignment to references (known targets, e.g. `FASTA` files of the 10 viruses/bacteria you are checking)
  _Objectives_: `BAM` files and simple visualizations
  _Actionable_: Yes (basic). As a next step, this can connect to the amplicon pipeline (for each `BAM` file), starting from _Step 3_.
- **Step 3b**: Alignment/matching against agnostic databases (such as Kraken, NR, k-mer based search etc)
  _Objectives_: Table of matches (`BLAST`-like tables) and simple visualizations (such as by taxonomy)
  _Actionable_: Yes (basic). 
- **Step 3c**: AMR detection and virulence factor, using specific AMR databases
  _Objectives_: List of AMR and virulence factor genes detected
  _Actionable_: Yes



# List of relevant software tools

In order to have a better assessment of the landscape, it's important to be aware of the various bioinformatic tools that exist, and fit in the above steps. For each tool we captured the following fields:


\begin{enumerate}
\item Tool Name
\item Version
\item Date of latest version
\item License
\item Goal / Objective of the tool
\item Expected Inputs
\item Produced Output
\item Source Code Location
\item Does it use external tools
\item Compatible to existing workflow systems (such as Galaxy, CWL, Snakemake, Nextflow, etc)
\item Available through package manager (ie bioconda, bioconductor, etc)
\item Scope (such as SARS-CoV-2, microbiome, AMR, monkeypox)
\item Is it standalone (i.e. runs on FASTQ file input), or does it require additional steps.
\item Citation of the tool (i.e. papers that have already used the tool)
\item Amplicon or Metagenomics
\item Which level of the workflow does it fall
\end{enumerate}



# Discussion




## Acknowledgements

Some of the authors were funded by ELIXIR, the research infrastructure for life-science data, to join the BioHackathon Europe.

## References




As part of the one week Biohackathion 2019 in Fukuoka Japan, we formed
a working group on logic programming for the biomedical sciences.
Logic programming is understood by many bioinformaticians when it is
presented in the form of relational SQL queries or SPARQL
queries. More advanced logic programming, however, is underutilized in
bioinformatics.  Prolog, for example, is a high-level programming
language that has its roots in first-order logic or first-order
predicate calculus.  Another example, miniKanren, is an embedded
Domain Specific Language for logic programming. Core miniKanren is
exceptionally simple, with only three logical operators and one
interface operator [@uses_method_in:reasoned2nd].

![Logic programming resolver traverses the solution space to find all matches \label{fig}](./logic-programming.png)

![An SVG example](./test.svg)

The introduction of logic programming is particularly relevant in the
context of multi-model data representations where data can be accessed
in memory as free data structures, but also on disk where data can be
represented as tables, trees (documents), and graphs. In
bioinformatics we can make use of all these different data sources and
have a query engine that can mine them all efficiently.  [@Chiba2015], KEGG OC, TogoVar, JCM, Allie, EBI
 BioSamples, UniProt, and DisGeNET [@Queralt2016]. [@agreesWith:reasoned2nd], PhD thesis
[@ByrdPhD], and [online](https://www.youtube.com/watch?v=eQL48qYDwp4)
[talks](https://www.youtube.com/watch?v=o3AHnyEf7IE).  FALDO model [@agreesWith:Bolleman2016]

