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


\begin{table}[H]
  \begin{center}
    \caption{Specific target workflow}
    \label{tab:tableTargetWorkflow}
    \begin{tabular}{p{0.1\linewidth} | p{0.3\linewidth} | p{0.3\linewidth} | p{0.3\linewidth}}
      \textbf{Nb} & \textbf{Step} & \textbf{Objectives} & \textbf{Actionable} \\
      \hline
      \textbf{0} & RT-PCR & Rough presence/absence of virus. Plus variants depending on probe. & Yes (basic) \\
      \textbf{1} & Sequencing & \texttt{FASTQ}/\texttt{FAST5} files - no further information & No \\
      \textbf{2} & Alignment to reference (incl. host removal and cleaning) & \texttt{BAM} file. & No \\
      \textbf{3} & Identify mutations & \texttt{VCF} files, list of mutations, pileups, etc & No \\
      \textbf{4} & Detect variants based on definitions & List of variants & Yes (variant level) \\
      \textbf{5} & Quantify variants based on definitions & List of variants with frequencies (should add up to 100\% per sample) & Yes (variant trends) \\
      \textbf{6} & Define new variants based on mutations & List of mutations not mapping to known definitions & Yes (emerging variants) \\
    \end{tabular}
  \end{center}
\end{table}



## Unknown target meta-genomics / -transcriptomics workflow

Omics WW Surveillance System - unknown target metagenomics/metatranscriptomics (depending on the type of target you are looking for)

\begin{table}[H]
  \begin{center}
    \caption{Unknown target workflow}
    \label{tab:tableUnknownTargetWorkflow}
    \begin{tabular}{p{0.1\linewidth} | p{0.3\linewidth} | p{0.3\linewidth} | p{0.3\linewidth}}
      \textbf{Nb} & \textbf{Step} & \textbf{Objectives} & \textbf{Actionable} \\
      \hline
      \textbf{0} & RT-PCR & \textbf{Not possible} / \textbf{Not applicable} & No \\
      \textbf{1} & Sequencing & \texttt{FASTQ}/\texttt{FAST5} files - no further information & No \\
      \textbf{2} & QC on reads (remove host sequences) & \texttt{FASTQ}/\texttt{FAST5} files - no further information & No  \\
      \textbf{3a} & Alignment to references (known targets, e.g. \texttt{FASTA} files of the top 10 viruses /bacteria you are checking against) & \texttt{BAM} files and simple visualizations. & Yes (basic). As a next step, this can connect to the amplicon pipeline (for each \texttt{BAM} file), starting from \emph{Step 3}. \\
      \textbf{3b} & Alignment/matching against agnostic databases (such as Kraken, NR, k-mer based search etc) & Table of matches (\texttt{BLAST}-like tables) and simple visualizations (such as by taxonomy). & Yes (basic) \\
      \textbf{3c} & AMR detection and virulence factor, using specific AMR databases. & List of AMR and virulence factor genes detected & Yes \\
    \end{tabular}
  \end{center}
\end{table}


# List of relevant software tools

In order to have a better assessment of the landscape, it's important to be aware of the various bioinformatic tools that exist, and fit in the above steps. For each tool we captured the following fields:

1. Tool/Workflow name
2. Goal / Objective of the tool
3. Expected Inputs
4. Produced Output
5. Targeted (Amplicon) or Untargeted (Meta-genomics/-transcriptomics)
6. Scope (such as SARS-CoV-2, microbiome, AMR, monkeypox)
7. Standalone (i.e. runs on FASTQ file input) tool, or intermediate tool (i.e it requires additional steps)
8. Corresponding step(s) of the workflow
9. Version
10. Date of latest version
11. License
12. Source Code
13. External tools used
14. Compatible to existing workflow systems (such as Galaxy, CWL, Snakemake, Nextflow, etc)
15. Available through package manager (ie bioconda, bioconductor, etc)
14. Citation of the tool (i.e. papers that have already used the tool)

We identified 21 tools/workflow:



\begin{table}[H]
  \begin{center}
    \caption{List of tools}
    \label{tab:tableListOfTools}
    \begin{tabular}{p{0.1\linewidth} | p{0.2\linewidth} | p{0.2\linewidth} | p{0.2\linewidth} | p{0.2\linewidth}}
      \textbf{Tool / Workflow name} & \textbf{Targeted / Untargeted} & \textbf{Scope} & \textbf{Corresponding Workflow step(s)} & \textbf{Papers that used it} \\
      \hline
      \textbf{Freyja} & & & &  [@Karthikeyan2022], [@SolisMoreira2022],[@Karthikeyan2021], \href{https://www.fda.gov/food/whole-genome-sequencing-wgs-program/wastewater-surveillance-sars-cov-2-variants}{Center for Food Safety and Applied Nutrition."Wastewater Surveillance for SARS-CoV-2 Variants". FDA (Jan. 2022)}  \\

    \end{tabular}
  \end{center}
\end{table}

--------------     ----------       -----    --------     -----------
Tool/Workflow      Targeted /    	  Scope    Workflow     Papers that 
name               Untargeted                step(s)      used it
--------------     ----------       -----    --------     -----------
Freyja                                                    [@Karthikeyan2022],
                                                          [@SolisMoreira2022],
                                                          [@Karthikeyan2021],
                                                          [Center for Food Safety and Applied Nutrition."Wastewater Surveillance for SARS-CoV-2 Variants". FDA (Jan. 2022)](https://www.fda.gov/food/whole-genome-sequencing-wgs-program/wastewater-surveillance-sars-cov-2-variants)

COJAC                                                     [@Jahn2022],
                                                          [@Karthikeyan2022], [JBC and Defra "Wastewater monitoring of SARS-CoV-2 variants in England: demonstration case study for Bristol (December 2020 to March 2021), 8 April 2021](https://www.gov.uk/government/publications/jbc-and-defra-wastewater-monitoring-of-sars-cov-2-variants-in-england-demonstration-case-study-for-bristol-december-2020-to-march-2021-8-april-20)

LCS                                                       [@Valieris2022],
                                                          [@Karthikeyan2022]

Kallisto                                                  [@Baaijens2021],
                                                          [Matei Anton, "Kallisto Repurposed: Using sequencing reads from the spike, nucleocapsid, and a middle region of nsp3 in the kallisto pipeline to better predict SARS-CoV-2 variants in wastewater", 2022](https://repository.tudelft.nl/islandora/object/uuid%3A990e42c3-e79f-4ff9-85ffa614554269bb) 

Alcov                                                     [@Ellmen2021]

SAM refiner                                               [Gregory2021],
                                                          [@Gregory2022],
                                                          [@Yaglom2022]

Pipes et al.                                              [@Pipes2022]

Gromstole

AG                                                        [@NGuessan2022]

Lineagespot                                               [@Pechlivanis2022]

PiGx                                                      [@Schumann2021]

Cowwid                                                    [@Jahn2021],
                                                          [Surveillance of SARS-CoV-2 genomic variants in wastewater](https://bsse.ethz.ch/cbg/research/computational-virology/sarscov2-variants-wastewater-surveillance.html)

Izquierdo-Lara et al.                                     [@IzquierdoLara2021] 

Galaxy wastewater amplicon workflow

Kraken

KRONA

Abricate

staramr

Mykrobe

Pathofact

ariba



# Discussion




## Acknowledgements

Some of the authors were funded by ELIXIR, the research infrastructure for life-science data, to join the BioHackathon Europe.

## References


