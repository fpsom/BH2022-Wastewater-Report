---
title: 'Exploring the landscape of the genomic wastewater surveillance ecosystem: a roadmap towards standardization'
title_short: 'Overview of the Genomic Wastewater Surveillance landscape'
tags:
  - Wastewater surveillance
authors:
  - name: Fotis Psomopoulos
    orcid: 0000-0002-8021-9162
    affiliation: 1
  - name: Konstantinos Kyritsis
    orcid: 0000-0001-8035-341X
    affiliation: 1
  - name: Ivan Topolsky
    orcid: 0000-0002-7561-0810
    affiliation: 2
  - name: Bérénice Batut
    orcid: 0000-0001-9852-1987
    affiliation: 3
  - name: Amy Heather Fitzpatrick
    orcid: 0000-0002-1883-0489
    affiliation: 4
  - name: Gabriele Leoni
    orcid: 0000-0002-4899-5284
    affiliation: 5
affiliations:
  - name: Institute of Applied Biosciences, Centre for Research and Technology Hellas, Thessaloniki, Greece
    index: 1
  - name: Computational Biology Group, SIB Swiss Institute of Bioinformatics, Basel,Switzerland
    index: 2
  - name: University of Freiburg, Germany
    index: 3
  - name: University College Dublin
    index: 4
  - name: European Commission, Joint Research Centre (JRC), Ispra, Italy
    index: 5
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

Nearly two years after the first report of SARS-CoV-2 in Wuhan, China, the COVID-19 pandemic has affected more than 485 million people. Wastewater surveillance has attracted extensive public attention during the SARS-CoV-2 pandemic, as a passive monitoring system to complement clinical genomic surveillance activities. Several methods are already in place that effectively facilitate the detection and quantification of viral RNA in wastewater samples, and concentrations in wastewater have been shown to correlate with trends in reported cases.

With exploratory projects having shown promise, it is now important to coordinate among initiatives to establish standards and build an inventory of the available software tools and services. This effort wil simplify the deployment of end-to-end genomic wastewater surveillance pipelines and increase the adoption of such promising monitoring methods across the wider community. The first step would be to identify and catalogue the relevant methodologies and bioinformatics workflows that are integral components of the lifecycle of genomic data derived from wastewater samples, combining into a coherent structure.

The main goal of this project has been to review, collate and offer a first attempt towards integrating, standardizing and reporting different approaches that are available for genomic wastewater surveillance. Leveraging the collective expertise of the [ELIXIR Wastewater Surveillance Working Group](https://www.covid19dataportal.org/partners?activeTab=Working%20groups), we focussed on creating a comprehensive landscape of components (e.g. modules, tools etc) that can be effectively utilized for end-to-end genomic wastewater surveillance pipelines.

<!--
# Results
-->

# Defining the key elements of an omic Wastewater Surveillance framework

One of the first activities of the project was to review and identify the possible questions that an omic Wastewater Surveillance is expected to address, keeping in mind that a key requirement of the system is to produce actionable results, i.e. information that can be directly consumed by public health experts. For example, `VCF` files cannot be considered as actionable, as they require particular expertise to be understood; on the other hand, variant frequencies in a given sample are actionable, as they provide sufficient information to a public health expert to follow up.

An indicative list of these questions are:

1. Is virus `v` present in the wastewater sample?

   Essentially this is a question of presence/absence that is traditionally addressed through RT-qPCR or equivalent methods. However, there are cases (such as the monkeypox virus) that RT-qPCR cannot disambiguate easily, therefore a sequencing step is required for confirmation. 

2. Does the virus ‘v’ vary seasonally? 

For example, many gastrointestinal viruses exhibit a strong seasonal peak during the winter in the northern hemisphere. Conversely, enteroviruses exhibit a strong peak during the summer period. This information can be used to inform public health agencies when specific intervention measures should be implemented. 

3. Is the variant `vv` present in the wastewater sample?

4. What is the longitudinal change of the variants?

   Essentially this is translated as identifying the trend of variant presence frequencies across multiple time points and samples.

5. What is the fitness advantage?

   This is one of the more advanced questions that could be addressed by wastewater surveillance, and involves the projection of the trajectory of a given variant in time and the calculation of a possible $R_e$.

6. What are potentially emerging variants?


# Standardizing definitions

Looking into viruses in particular, one of the main challenges is still the definition of variants. Typically, a viral Family is approach is taken with direction coming from consortium groups such as the International Committee on Taxonomy of Viruses (ICTV) or sub-specialist groups at genus level. Generally, variants have one to multiple different Single Nucleotide Variations (SNVs) and short Insertion-Deletion mutations (InDels) compared the closest known strain within a viral species. Nevertheless, variant indicates that there are no known phenotypic differences between the closest known strain and the variant. The challenge is defying how many SNVs and InDels result in variant designation, and this has lead to varying definitions and applications of the term. Phenotypic differences result in the designation of new strain.  

Public databases (i.e. public health registries and specialized repositories such as [outbreak.info](https://outbreak.info/)) can be used to monitor variants. Nevertheless, given the multitude of potential variants and respective definitions, more often than not, tools use a custom list of pre-selected definitions (or even simplified versions of the same definitions). However, this approach implies that there is always going to be a human factor in the process, assessing which definitions (or parts of definitions) will be used.

In either case, it is important to identify what would be the minimal information expected as input to a federated omics wastewater surveillance system, i.e. reaching a consensus on how to tackle common definitions (looking also at FAIR definitions.)


Definition: Antimicrobial Resistance


Definition: Virulence factor


# Considerations on Wastewater data analyses

Due to the intrinsic nature of wastewater samples, it is common to have only partial genomic data related to the target organism (i.e., the whole genome sequence of the organism in not available in the data). This prohibits reliable and trustuble lineage identification. In this situation, the detection of specific mutations, with potential impacts on the organism pathogenicity/trasmissibility, could be used as a powerful signal for policy purposes (i.e., identification of relevant Spike variants in SARS-CoV-2).
In the presence of complete genomic data related to the targeted organism (i.e., the whole genome sequence of the organism is present within the wastewater sample), the process of identify new lineages based on mutation data can be, in principle, achieved from wastewater data. However, this should be strongly discouraged as researchers would need to be extremely confident on the pureness of the original sample (i.e., it do not contains multiple lineages/variants). The ultimate risk would be to create a false lineage, not existing in nature, that would consists of mutations from the different lineages present in the sample. This in turn would be reflected in the lineage databases, with the potential risk of propagating to other studies/analyses with negative effects.


# Omic Wastewater Surveillance

We identify three stages of omic Wastewater Surveillance workflows; thought they are not necessarily concurrent:

- Design and in-silico validation of primers and/or benchmarking bioinformatic pipelines
- specific target (e.g. single virus and variants), typically amplicon based, and
-  unknown target metagenomics / metatranscriptomics
	- Shotgun metagenomics or metratranscriptomics can include virus enrichment or       host depletion steps prior to High Throughput Sequencing

For each of these workflows, we have identified the key phases involved (not including the sampling and wet-lab partis of the process).

## In-silico validation
Slightly different approaches are required for in-silico validation for targeted and non-targeted approaches. These are clearly outlined in two separate tables, whilst the final table in this section contains the relevant steps that are common to both approaches. 

### Specific target (tiling amplicon-based) 
Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | Generation of comprehensive viral database| Complete representation of genetic diversity for target virus(es)  | No
1 | In-silico PCR with primers| FASTA file of amplicons  | No
2 | Classification accuracy | Comparison of performance of primers for specific target(s)| Yes


### Specific target (shotgun metagenomics) 
Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | Generation of comprehensive viral database| Complete representation of genetic diversity for target virus(es)  | No
1 | Generation of background DNA/RNA wastewater database | Accurate representation of matrix composition ( i.e. influent or effluent) | No 
2 | Model wastewater sample composition | Accurately represent the viral composition in a wastewater dataset prior to sequencing, incorporating relevant information such as enrichment/depletion steps, composite or passive sample type | No

### Final approach for both targeted and non-targeted in-silico approaches
Nb | Step |	Objective | Actionable
---|------|-----------|------------
3 | In-silico simulation of platform specific sequencing reads | FASTQ/FAST5 files | no
4 | Application of bioinformatic workflows/pipelines | Various outputs - virus classification variants detected and composition and presence/absense of clinically relevant mutations | No
5 | Comparison to ground truth - Classification accuracy and compositional similarity/dissimilarty | Yes

## Omics WW Surveillance System - specific target (e.g. single virus + variants) / tiling amplicon based

Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | RT-PCR | Rough presence/absence of virus. Plus variants depending on probe. | Yes (basic)
1 | Sequencing | Produce raw reads data in `FASTQ`/`FAST5` format | No
2 | Quality control step | trimming/reads quality assesment | No
3 | Alignment to reference (incl. host removal and cleaning) | `BAM` file | No 
4 | Identify mutations | `VCF` files, list of mutations, pileups, etc | Yes 
5 | Detect variants based on definitions | List of variants | Yes (variant level)
6 | Quantify variants based on definitions | List of variants with frequencies (should add up to 100% per sample) | Yes (variant trends)
7 | Define new variants based on mutations | List of mutations not mapping to known definitions | Yes (emerging variants)
8 | Clinically relevant mutation | Interpret mutations from VCF | Tracking of clinically relevent mutations, independent of variant designation - e.g. antibody evasion, drug resistance | Yes

## Unknown target meta-genomics / -transcriptomics workflow

Omics WW Surveillance System - unknown target metagenomics/metatranscriptomics (depending on the type of target you are looking for)

Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | RT-qPCR | **Not applicable** | No
1 | Sequencing | Produce raw reads data in `FASTQ`/`FAST5` | No
2 | QC on reads | trimming/reads quality assesment | No
3a | Alignment to references (incl. Host removal and cleaning; alignment vs known targets, e.g. `FASTA` files of the top 10 viruses /bacteria you are checking against) | `BAM` files and simple visualizations. | Yes (basic). As a next step, this can connect to the amplicon pipeline (for each `BAM` file), starting from _Step 3_. 
3b | Alignment/matching against agnostic databases (such as Kraken, NR, k-mer based search etc) | Table of matches (`BLAST`-like tables) and simple visualizations (such as by taxonomy). | Yes (basic)
3c | AMR detection and virulence factor, using specific AMR databases. | List of AMR and virulence factor genes detected | Yes
3d | Assembly based approaches (SPades) and DIAMOND/BLAST DB search for taxonomy classification | Assembled virus with taxonomic classification | yes
4 | Specific target (amplicon-based) workflow (from point 4) | If Specific target can be identified by 3a/3b/3d, Specific target (amplicon-based) workflow can be used from point 4 | yes

# List of relevant software tools

In order to have a better assessment of the landscape, it's important to be aware of the various bioinformatic tools that exist, and fit in the above steps. We have generated two tables to outline the tools useful for in-silico validation, as well as those tools used for the bioinformatic processing and analysis of High Throughput Sequencing data from wastewater samples. The tables are structured as follows: 
1. Tool/Workflow name
2. Citation of the tool (i.e. papers that have already used the tool)

We identified 11 tools for in-silico validation
Tool name  | Citation
-------------------|---------------------
InsilicoSeq | https://github.com/HadrienG/InSilicoSeq
ART | https://www.niehs.nih.gov/research/resources/software/biostatistics/art/index.cfm
BEAR | https://github.com/sej917/BEAR
Grinder | https://github.com/zyxue/biogrinder
NanoSim2 | https://github.com/bcgsc/NanoSim
BadRead | https://github.com/rrwick/Badread
PBSIM | https://github.com/pfaucon/PBSIM-PacBio-Simulator
longsiland | https://github.com/bioinform/longislnd
In-silico-pcr | https://github.com/egonozer/in_silico_pcr
Silica | https://github.com/gear-genomics/silica
Yardstick | https://yardstick.tidymodels.org/

We identified 36 tools/workflow for bioinformatic processing and analysis of HTS data from wastewater

Tool/Workflow name  | Citation
-------------------|---------------------
Freyja  [@Karthikeyan2022], [@SolisMoreira2022], [@Karthikeyan2021], [Center for Food Safety and Applied Nutrition."Wastewater Surveillance for SARS-CoV-2 Variants". FDA (Jan. 2022)](https://www.fda.gov/food/whole-genome-sequencing-wgs-program/wastewater-surveillance-sars-cov-2-variants)
COJAC | [@Jahn2022]
LolliPop  | [@Dreifuss2022]
LCS | [@Valieris2022], [@Karthikeyan2022]
Kallisto |  [@Baaijens2021], [Matei Anton, "Kallisto Repurposed: Using sequencing reads from the spike, nucleocapsid, and a middle region of nsp3 in the kallisto pipeline to better predict SARS-CoV-2 variants in wastewater", 2022](https://repository.tudelft.nl/islandora/object/uuid%3A990e42c3-e79f-4ff9-85ffa614554269bb) 
Alcov | [@Ellmen2021]
SAM refiner |    [@Gregory2021],[@Gregory2022],[@Yaglom2022]
Pipes et al. |    [@Pipes2022]
Gromstole |   https://github.com/PoonLab/gromstole
AG |    [@NGuessan2022]
Lineagespot  |    [@Pechlivanis2022]
PiGx  |    [@Schumann2021]
Izquierdo-Lara et al.  |    [@IzquierdoLara2021] 
Galaxy wastewater amplicon workflow |   
Kraken | 
Kraken2 | https://genomebiology.biomedcentral.com/articles/10.1186/s13059-019-1891-0
KRONA |   https://github.com/marbl/Krona
Abricate |  https://github.com/tseemann/abricate
staramr |  https://github.com/phac-nml/staramr 
Mykrobe |    https://github.com/Mykrobe-tools/mykrobe
Pathofact | https://microbiomejournal.biomedcentral.com/articles/10.1186/s40168-020-00993-9
ariba |   https://github.com/sanger-pathogens/ariba
Hostile | https://github.com/bede/hostile
Virstrain | https://genomebiology.biomedcentral.com/articles/10.1186/s13059-022-02609-x|
ViralClust | https://github.com/klamkiew/viralclust
VIRify | https://github.com/EBI-Metagenomics/emg-viral-pipeline
DeepVirFinder | https://github.com/jessieren/DeepVirFinder
Virulign | https://github.com/rega-cev/virulign
Palmscan | https://github.com/rcedgar/palmscan
coronaSPades | https://academic.oup.com/bioinformatics/article/38/1/1/6354349
viralrecon | https://github.com/nf-core/viralrecon
Viral-ngs | https://viral-ngs.readthedocs.io/en/latest/
ViralMSA | https://github.com/niemasd/ViralMSA
VirSorter2 | https://github.com/jiarong/VirSorter2
ViralFlye | https://github.com/Dmitry-Antipov/viralFlye
CheckV | https://bitbucket.org/berkeleylab/CheckV


# Use-case

## V-pipe


Building on the above survey of the landscape, we have integrated tools into an end-to-end workflow that is published on Elixir’s WorkflowHub platform. This was accomplilshed by combining the following tools:

V-pipe is a bioinformatics workflow for the analysis of sequencing data of viral
samples exhibiting genomic diversity, either within hosts in clinical samples or
among hosts in environmental samples. It has been an SIB Software Resource
since 2017.


## Galaxy


[JBC and Defra "Wastewater monitoring of SARS-CoV-2 variants in England: demonstration case study for Bristol (December 2020 to March 2021), 8 April 2021](https://www.gov.uk/government/publications/jbc-and-defra-wastewater-monitoring-of-sars-cov-2-variants-in-england-demonstration-case-study-for-bristol-december-2020-to-march-2021-8-april-20)

>> Building on this landscape, this project will attempt a first integration of selected modules within the ELIXIR Tools Platform ecosystem (Galaxy, bio.tools, WorkflowHub etc).
# Discussion

The main goal of this project was to integrate, standardize and report the different approaches available for genomic wastewater surveillance. With our exploration, we highlighted several aspects that, to us, are critical while analysing wastewater data. These aspects range from the intrinsic nature of the wastewater specimen till the interpretation of the results, with analyses workflows and tools displaying a pivotal role. To tackle these features, we identified three stages of omic Wastewater Surveillance workflows and created a comprehensive landscape of components (e.g. modules, tools, etc) that can be effectively utilized for end-to-end genomic wastewater surveillance pipelines. The three omic Wastewater surveillance workflows can be divided into:

- Design and in-silico validation of primers and/or benchmarking bioinformatic pipelines.
- Specific target analyses(e.g. single virus and variants), typically amplicon based.
- Unknown target metagenomics / metatranscriptomics analyses

For each of these workflows, we have identified the key phases involved (not including the sampling and wet-lab partis of the process). As several different tools can be selected to process High-Throughput Sequencing data from wastewater (even for the same phase), a comprehensive bioinformatic benchmarking is required to compare and contrast the resulting outputs. This requirement is only exacerbated by the presence of different methodologies, like the amplicon-based and metagenomics/metatranscriptomics approaches.

It must be taken into consideration that the outcome and the interpretation of the analyses is heavily dependent on the workflow applied from wet-lab through to bioinformatics (dry-lba approaches) and on the original sample. For instance, lineage assignation steps can be considered reliable and trustable only when the complete target organism genome can be found in the wastewater sample.   



It is important to exercise caution in the interpretation of the output data. Output data is heavily dependent on the workflow applied from wet-lab through to bioinformatic (dry-lab approaches). 
There are a variety of tools/workflows available for bioinformatics processing of High Throughput Sequencing data from wastewater. A comprehensive bioinformatic benchmarking is required to compare and contrast both tools and approaches for targeted and non-targeted HTS approaches. 
Wastewater based epidemiology is a powerful tool for public health as demonstrated in the use-case. In order to apply it broadly for viral surveillance, minimum information for reporting of WPE results i.e MIWPE should be established. 
 
## Acknowledgements

Some of the authors were funded by ELIXIR, the research infrastructure for life-science data, to join the BioHackathon Europe.

## References
