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

1. Tool Name
2. Version
3. Date of latest version
4. License
5. Goal / Objective of the tool
6. Expected Inputs
7. Produced Output
8. Source Code Location
9. Does it use external tools
10. Compatible to existing workflow systems (such as Galaxy, CWL, Snakemake, Nextflow, etc)
11. Available through package manager (ie bioconda, bioconductor, etc)
12. Scope (such as SARS-CoV-2, microbiome, AMR, monkeypox)
13. Is it standalone (i.e. runs on FASTQ file input), or does it require additional steps.
14. Citation of the tool (i.e. papers that have already used the tool)
15. Amplicon or Metagenomics
16. Which level of the workflow does it fall



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
have a query engine that can mine them all efficiently.

Logic programming is well-suited for biological research. Essentially,
a researcher writes a number of statements that include variables
representing unknown information.  The logic engine then goes through
the solution space (all data) to find possible matches (see figure
\ref{fig}). Much more detail on the rationale and implementations of
miniKanren and logic programming are well summarized in Byrd's book
\emph{The Reasoned Schemer, Second Edition} [@agreesWith:reasoned2nd], PhD thesis
[@ByrdPhD], and [online](https://www.youtube.com/watch?v=eQL48qYDwp4)
[talks](https://www.youtube.com/watch?v=o3AHnyEf7IE).

The `Logic Programming' working group at the 2019 edition of the
annual Japanese BioHackathon applied logic programming to various problems.
The working group:
\begin{itemize}
\item researched state-of-the-art mapping between graph stores and logic programming;
\item created methods for bridging between SPARQL and in-memory data representations using Prolog;
\item extended the Biolink model;
\item and added Relational Biolink type inference for mediKanren.
\end{itemize}

<!--
# Results
-->

## Research of state-of-the-art logic programming facilities for SPARQL

The working group researched current solutions for combining logic
programming with SPARQL.
[ClioPatria](http://www.semantic-web-journal.net/system/files/swj1074.pdf)
is an in-memory RDF quad-store tightly coupled with SWI-Prolog by Jan
Wielemaker, the main author of SWI-Prolog
[@WielemakerBHO15]. SWI-Prolog is published under a BSD license, and
there even exist bindings for
[ClioPatria and Python](http://wi.hwtk.de/WLP2018/Papers/WLP_2018_paper_4.pdf),
for example, although we were unable to locate the source code. We
think ClioPatria and SWI-Prolog are particularly useful for teaching,
and for (in-memory) semantic web applications. SWI-Prolog comes with
client libraries for SQL and SPARQL queries.

## Accessing biological databases using SPARQLProg

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work
-->

A number of biological databases make their data available in RDF
format, supporting SPARQL access---for example,
[Uniprot](https://www.uniprot.org/),
[NCBI Pubchem](https://pubchemdocs.ncbi.nlm.nih.gov/rdf) and the
[EBI RDF platform](https://www.ebi.ac.uk/rdf/).
SPARQL provides a subset of what logic programming can do.
However, SPARQL queries lack the property of composability and there is no way to
reuse modular components across queries.  For example, to execute a
range query on a genomic region using the FALDO model [@agreesWith:Bolleman2016]
requires authoring a complex query over many triples. If we then wish
to reuse parts of that query in a more complex query, we have to
manually compose them together.

The working group added codes to
[SPARQLProg](https://github.com/cmungall/sparqlprog) which provides a
way to define modular query components using logic programming.
SPARQLProg is written in
SWI-Prolog and has a Python interface library. All code has been made
available in the example directory of
SPARQLProg which provides
sophisticated mapping of logic queries to SPARQL.

For example, a 4-part predicate `feature_in_range` can be composed
with a binary \
`has_mouse_ortholog` predicate:

```
    feature_in_range(grch38:"X", 10000000, 20000000, HumanGene),
    has_mouse_ortholog(HumanGene, MouseGene)
```

This will compile down to a more complex SPARQL query, and execute it against a remote endpoint.

SPARQLProg now includes bindings for many common biological SPARQL
endpoints. As part of this hackathon we developed codes to access RDF
databases of MBGD [@Chiba2015], KEGG OC, TogoVar, JCM, Allie, EBI
 BioSamples, UniProt, and DisGeNET [@Queralt2016]. Future work includes using these
Prolog codes as building blocks for integrative analysis.

## Extending the Biolink Model

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work
-->

The [Biolink Model](https://github.com/biolink/biolink-model) (see
above) is a data model developed for representing biological and
biomedical knowledge. It includes a schema and generated objects for
the data model and upper ontology. The BioLink Model was designed with
the goal of standardizing the way information is represented in a
graph store, regardless of the formalism used. The working group
focused on extending this model to support representation of a wide
variety of knowledge.

The following tasks were accomplished as part of the BioHackathon:

\begin{enumerate}
\item Represent datasets and their related metadata
\item Represent family and pedigree information to support clinical knowledge
\item Make the provenance model more rich and descriptive
\end{enumerate}

For future work, the group will ensure that the new classes added to
the model will have appropriate mappings to other schemas and
ontologies.

##  Relational Biolink type inference for mediKanren

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work

* Remote member Nada Amin, Chris Mungall, Deepak Unni, Will Byrd

-->

miniKanren is an embedded Domain Specific Language for logic
programming.  The goal was to implement a relational type inferencer
for the [Biolink Model](https://biolink.github.io/biolink-model/) in
miniKanren, which can be integrated into mediKanren. The working group
added a `yaml` subdirectory to the mediKanren GitHub page, and created
multiple files in https://github.com/webyrd/mediKanren/yaml where
`yaml2sexp.py` generates the `biolink.scm` file which contains an
s-expression version of the Biolink yaml file. `yaml.scm` contains
miniKanren relations, and Chez Scheme code that generates miniKanren
relations based on `biolink.scm`. These are giant miniKanren `conde`
clauses that can be thought of as relational tables.  `yaml.scm` also
contains tests for the relations.

Future work includes:

1. integrating this work into the Racket mediKanren code;
2. integrating with the data categories in the KGs;
3. and creating query editor with decent type error messages, autocompletion,
   query synthesis, etc.

# Discussion

The working group concluded that there is ample scope for logic
programming in bioinformatics. Future work includes expansion of
accessing semantic web databases using SPARQLProg, expanding the
BioLink model, and adding dynamic SPARQL support to miniKanren.

## Acknowledgements

We thank the organizers of the NBDC/DBCLS BioHackathon 2019 for
travel support for some of the authors.

## References
