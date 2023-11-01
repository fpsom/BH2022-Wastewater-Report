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

Nearly two years after the initial report of SARS-CoV-2 in Wuhan, China, the COVID-19 pandemic has affected over 485 million individuals. Wastewater surveillance has garnered substantial attention as a passive monitoring system to complement clinical genomic surveillance activities during the SARS-CoV-2 pandemic. Several effective methods are now in place for detecting and quantifying viral RNA in wastewater samples, and it is evident that RNA concentrations in wastewater correlate with reported case trends.

Exploratory projects have demonstrated the potential of Wastewater Based Epidemiology (WBE), nevertheless it is imperative to coordinate efforts, establish standards, and create a catalog of available software tools and services. This coordination will streamline the deployment of end-to-end genomic wastewater surveillance pipelines and promote the adoption of these monitoring methods within the broader scientific community. The initial step involves identifying and cataloging the challenges of working with wastewater HTS and the pertinent methodologies and bioinformatics workflows essential for managing genomic data from wastewater samples, thus forming a coherent structure.

The primary objective of this project was to systematically review, compile, and initiate the integration, standardization, and documentation of diverse approaches for genomic wastewater surveillance. Drawing on the expertise of the [ELIXIR Wastewater Surveillance Working Group](https://www.covid19dataportal.org/partners?activeTab=Working%20groups), our focus was to create a comprehensive framework of components, including modules and tools, to facilitate the practical implementation of end-to-end genomic wastewater surveillance pipelines.

<!--
# Results
-->

# Defining the key elements of an omic Wastewater Surveillance framework

One of the project's initial tasks involved a comprehensive review to identify the pertinent questions that omic Wastewater Surveillance should aim to answer. A fundamental criterion for this system is its ability to generate actionable results, which are insights that can be readily comprehended and utilized by public health experts. To illustrate, `VCF` files, with their specialized content, cannot be categorized as actionable since they necessitate specific expertise for interpretation. In contrast, variant frequencies within a given sample represent actionable data, as they provide public health experts with readily understandable information for further actions and decisions.

An indicative list of these questions are:

1. Is virus `v` present in the wastewater sample?

Essentially this is a question of presence/absence that is traditionally addressed through RT-qPCR or equivalent methods. 

2. Does the virus ‘v’ vary seasonally? 

For example, many gastrointestinal viruses exhibit a strong seasonal peak during the winter in the northern hemisphere. Conversely, enteroviruses exhibit a strong peak during the summer period. This information can be used to inform public health authorities when specific intervention measures should be implemented. 

3. Is the variant `vv` present in the wastewater sample?

4. What is the longitudinal change of the variants?

This question seeks to determine how the frequency of variants changes across different time points and samples.

5. What is the fitness advantage?

This is one of the more advanced questions that could be addressed by wastewater surveillance, and involves the projection of the trajectory of a given variant in time and the calculation of a possible $R_e$.

6. What are potentially emerging variants?


# Standardizing definitions

## Variants
Looking into viruses in particular, one of the main challenges is still the definition of variants. Typically, for each different viral family, a different approach is taken with directions coming from consortium groups such as the International Committee on Taxonomy of Viruses (ICTV) or sub-specialist groups at genus level. Generally, variants have one to multiple different Single Nucleotide Variations (SNVs) and short Insertion-Deletion mutations (InDels) compared to the closest known strain within a viral species. Nevertheless, variant indicates that there are no known phenotypic differences between the closest known strain and the variant. The challenge is in defining how many SNVs and InDels result in variant designation, and this has lead to varying definitions and applications of the term. Phenotypic differences should theoretically result in the designation of new strain.  

Public databases (i.e. public health registries and specialized repositories such as [outbreak.info](https://outbreak.info/) or [CovSpectrum](https://cov-spectrum.org/)) can be used to monitor variants for some viruses such as SARS-CoV-2 or Mpox. Nevertheless, given the multitude of potential variants and respective definitions, more often than not, tools use a custom list of pre-selected definitions (or even simplified versions of the same definitions). This approach implies that there is always a human factor in the process, assessing which definitions (or parts of definitions) will be used.

In either case, it is important to identify what would be the minimal information expected as input to a federated omics wastewater surveillance system, i.e. reaching a consensus on how to tackle common definitions, for example FAIR definitions.

## Antimicrobial Resistance

Antimicrobial resistance (AMR) is the phenomenon where microbes, either through mutations or the transfer of genes, acquire the capability to withstand the effects of antimicrobial agents that were previously effective in treating them. In simpler terms, AMR is the process by which microbes become resistant to drugs that used to work against them.

Antimicrobial resistance (AMR) in bacteria arises through several mechanisms. Bacteria can naturally develop resistance by accumulating genetic mutations, particularly in the genes encoding the target proteins of antimicrobial agents. These mutations can render the drugs less effective. Additionally, bacteria can share resistance genes through horizontal gene transfer mechanisms such as conjugation, transformation, and transduction, allowing the rapid spread of resistance within bacterial populations. Plasmids, small circular DNA molecules, often carry these resistance genes and can be readily transferred between bacteria. Some bacteria possess efflux pumps that actively expel antimicrobial agents from within the bacterial cell, reducing drug concentrations and efficacy. Bacterial biofilm formation provides a protective matrix that shields bacteria from antimicrobial agents. Enzymatic inactivation, wherein bacteria produce enzymes that degrade antibiotics, is another strategy they employ. Therefore, the challenge within a metagenomics framework is recognizing the potential AMR mechanisms that a genome or assembly could employ to evade antimicrobials, without the complete environmental context. 

Furthermore, presence of specific mutations or plasmids does not infer AMR as it is not always clear from shotgun metagenomics whether those specific regions/genes can be transcribed. Metatranscriptomics can provide a clearer resolution on potential AMR, but the gold standard remains phenotypic assays in the wet-lab. 

## Viral fitness
Viral fitness is a concept in virology that refers to the ability of a virus to successfully replicate and propagate within a host organism or population of hosts. It encompasses various aspects of a virus's biological characteristics, such as its reproductive rate, transmission potential, and adaptability to changing environments. A virus with high fitness can efficiently reproduce, spread from host to host, and adapt to selective pressures, often resulting in a more successful and prevalent infection. 

Assessing viral fitness through shotgun metagenomics and metatranscriptomics provides valuable insights into the dynamics of viral populations within complex microbial communities. By tracking changes in viral genomic content, such as the accumulation of mutations or the presence of fitness-enhancing mutations, viral fitness can be indirectly inferred. Moreover, metatranscriptomics is particularly well-suited for studying RNA viruses as RNA is the primary target rather than DNA. Once again, the challenge is the definition of what is fitness-enhancing mutations. In order to interpret genomic data for viral-fitness, mutations need to be studied within a wet-lab context and documented within literature. During specific scenarios, such as pandemics or epidemics these wet-lab studies are challenging to conduct within short time-frames and results often lag behind the evolving evolutionary landscape of the virus. Inference through phylogenomics has improved our understanding of which mutations may play a role in viral-fitness but this is a field lacking curated databases for broad annotation of viral genomes. 

# Considerations on Wastewater data analyses

Wastewater data analysis presents unique challenges due to the partial genomic data often found in samples. In many cases, the complete genome sequence of the target organism may not be available, making reliable variant identification challenging. The detection of specific mutations with potential implications for the organism's viral fitness can serve as a valuable signal for public health measures. For instance, it can aid in the identification of significant Spike variants in viruses like SARS-CoV-2. Nevertheless, care should be taken to implement quality control parameters that limit the missed or mis designation of variants i.e. X coverage, quality score cut-offs, contig length, N repeated detection. Specialised tools for variant designation and lineage assignment should be used for highly fragmented data from wastewater, water or food samples. 

# Omic Wastewater Surveillance

We identify two stages of omic Wastewater Surveillance workflows; with stage two consisting of two approaches:

- Design and in-silico validation of primers and/or benchmarking bioinformatic pipelines
- Real world application
-  specific target (e.g. single virus and variants), typically amplicon based, and
-  unknown target metagenomics / metatranscriptomics
		- Shotgun metagenomics or metratranscriptomics can include virus enrichment or       host depletion steps prior to High Throughput Sequencing

For each of these stages and approaches, we have identified the key phases involved (not including the sampling and wet-lab partis of the process).

## In-silico validation
Slightly different approaches are required for in-silico validation for targeted and non-targeted approaches. These are clearly outlined in two separate tables, whilst the final table in this section contains the relevant steps that are common to both approaches. 

### Specific target (tiling amplicon-based) 
Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | Generation of comprehensive viral database| Complete representation of genetic diversity for target virus(es)  | No
1 | _In-silico_ PCR with primers| FASTA file of amplicons  | No
2 | Classification accuracy | Comparison of performance of primers for specific target(s)| Yes


### Specific target (shotgun metagenomics) 
Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | Generation of comprehensive viral database| Complete representation of genetic diversity for target virus(es)  | No
1 | Generation of background DNA/RNA wastewater database | Accurate representation of matrix composition ( i.e. influent or effluent) | No 
2 | Model wastewater sample composition | Accurately represent the viral composition in a wastewater dataset prior to sequencing, incorporating relevant information such as enrichment/depletion steps, composite or passive sample type | No

### Final approach for both targeted and non-targeted _in-silico_ approaches
Nb | Step |	Objective | Actionable
---|------|-----------|------------
3 | _In-silico_ simulation of platform specific sequencing reads | FASTQ/FAST5 files | no
4 | Application of bioinformatic workflows/pipelines | Various outputs - virus classification variants detected and composition and presence/absense of clinically relevant mutations | No
5 | Comparison to ground truth - Classification accuracy and compositional similarity/dissimilarty | Yes

## Omics WW Surveillance System - specific target (e.g. single virus + variants) / tiling amplicon based

Nb | Step |	Objective | Actionable
---|------|-----------|------------
0 | RT-PCR | Rough presence/absence of virus. Plus variants depending on primer. | Yes (basic)
1 | Sequencing | Produce raw reads data in `FASTQ`/`FAST5` format | No
2 | Quality control step | trimming/reads quality assesment | No
3 | Alignment to reference (incl. host removal and cleaning) | `BAM` file | No 
4 | Identify mutations | `VCF` files, list of mutations, pileups, etc | No 
5 | Detect variants based on definitions | List of variants | Yes (variant level)
6 | Quantify variants based on definitions | List of variants with frequencies (should add up to 100% per sample) | Yes (variant trends)
7 | Define new variants based on mutations | List of mutations not mapping to known definitions | Yes (emerging variants)
8 | Clinically relevant mutation | Interpret mutations from VCF | Tracking of clinically relevent mutations, independent of variant designation - e.g. antibody evasion, drug resistance | Yes (prevalence of virulence factors)

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

In order to have a better assessment of the landscape, it's important to be aware of the various bioinformatic tools that exist, and fit in the above steps. We have generated two tables to outline the tools useful for _in-silico_ validation, as well as those tools used for the bioinformatic processing and analysis of High Throughput Sequencing data from wastewater samples.

We identified 12 tools for _in-silico_ validation

Tool name  | Citation
-------------------|---------------------
InsilicoSeq | [@insilicoseq]
ART | [@art]
BEAR | [@bear]
Grinder | [@grinder]
NanoSim2 | [@nanosim]
NEAT | [@neat]
BadRead | [@badread]
PBSIM | [@pbsim]
longsiland | [@longislnd]
_In-silico_-pcr | [@in_silico_pcr]
Silica | [@silica]
SWAMPy | [@swampy]

We identified 36 tools/workflow for bioinformatic processing and analysis of HTS data from wastewater

Here's the table reordered by action category:

Tool/Workflow name  | Action |  Citation
-------------------|-----------|-----------------
Hostile | Host removal | [@hostile]
viralrecon | Workflow for assembly and variant detection | [@nf-coreviralrecon]
Viral-ngs | Workflow for assembly and taxonomic classification |[@viral-ngs]
VIRify | Detection, annotation, and taxonomic classification | [@virify_2023]
Galaxy wastewater amplicon workflow | 
Wastewater_surveillance_pipeline |  Variant composition &  lineage assignment | [@NGuessan2022]
coronaSPades | Virus assembler |[@coronaspades]
Kraken | taxonomic classification | [@kraken]
Kraken2 | taxonomic classification | [@Kraken2]
VirSorter2 | taxonomic classification | [@virsorter]
KRONA |  taxonomic visulisation | [@krona]
Abricate | AMR or virulence gene prediction | [@abricate]
staramr | AMR prediction | [@staramr]
Mykrobe | AMR prediction & phylogenetics |[@mykrobe]
Pathofact | AMR or virulence gene prediction | [@pathofact]
ariba | AMR prediction and MLST typing | [@ariba]
ViralClust | Virus specific clustering | [@viralclust]
ViralMSA | Multiple sequence alignment | [@viralmsa]
DeepVirFinder | Virus detection |[@deepvirfinder]
Virulign | Codon-correct pairwise alignments | [@virulign]
Palmscan | Virus detection and taxonomic classification | [@palmscan]
SAM refiner |  Variant extraction |  [@Gregory2021],[@Gregory2022],[@Yaglom2022]
Virstrain | Variant detection | [@virstrain]
COJAC | Variant detection | [@Jahn2022]
Lineagespot  |  Variant composition &  lineage assignment | [@Pechlivanis2022]
Alcov | Variant composition | [@Ellmen2021]
Gromstole | Variant composition |  [https://github.com/PoonLab/gromstole](https://github.com/PoonLab/gromstole)
LolliPop  | Variant Visualization | [@Dreifuss2022]
Freyja  |   Lineage assignment  | [@Karthikeyan2022]
LCS | Lineage composition | [@Valieris2022], [@Karthikeyan2022]
Kallisto | Fast pseudoalignment quantification | [@Baaijens2021]
ViralFlye | long-read Metagenome Assembled Viruses (MAVs)| [@viralflye]
CheckV | Quality control of MAVs | [@checkv]


# Use-case

Integrated workflows or pipelines offer a streamlined and cohesive approach to data analysis, enhancing the efficiency and reliability of the entire process, in contrast to the fragmented nature of working with independent tools. The advantage of integrated workflows lies in their ability to seamlessly connect different stages of analysis, ensuring data consistency and reducing the risk of errors or data loss that can occur when manually transferring data between separate tools. In contrast, relying on independent tools often involves intricate data handling and increased risk of compatibility issues, which can lead to time-consuming and error-prone tasks in data management and analysis. Integrated workflows address these challenges, providing a more robust and efficient solution for complex data processing and analysis tasks. Furthermore, this reduces the specialist knowledge required to run specific bioinformatics pipelines, a important component for standardised, accredited WBE or genomic surveillance in general. 

We have demonstrated two case studies of integrated pipelines below relevant to viral surveillance within a WBE context. 

## V-pipe: A Comprehensive Bioinformatics Workflow

In response to the evolving landscape of viral genomic diversity analysis, we have developed an end-to-end bioinformatics workflow, V-pipe, now hosted on Elixir's WorkflowHub platform. This integration brings together essential components for the analysis of sequencing data derived from viral samples, whether they exhibit genomic diversity within clinical hosts or across hosts in environmental samples.

###  Key Components

- **V-pipe**: An Integrated Bioinformatics Workflow
V-pipe is an integrated bioinformatics workflow designed to address the evolving challenges in the analysis of viral genomic diversity. It has been a pivotal resource within the SIB Swiss Institute of Bioinformatics (Swiss Elixir Node) since 2017 [@Fuhrmann2023]. V-pipe covers the initial preprocessing steps, including quality control using prinseq, configurable alignment employing bwa2 for SARS-CoV-2, and mutation identification via pileup generation and results summarization in TSV format.

- **COJAC**: Early Detection of Emerging Variants
COJAC is a crucial tool for the early detection of emerging variants, particularly useful for monitoring the spread of viral variants. It leverages the co-occurrence of signature mutations and has been instrumental in tracking the Omicron variant's distribution across 450 sites in the UK, as documented in a technical briefing [@UKHSA-TechnicalBriefing30].

-**LolliPop**: Variant Deconvolution and Relative Abundance Estimation
LolliPop is specifically developed for variant deconvolution and the estimation of relative abundances, even when dealing with shared mutations among variants and complex sequencing data. It utilizes a kernel-based deconvolution approach and capitalizes on time series information in the sample set.

These three key components were seamlessly integrated during a recent biohackathon, with real-world data from the Swiss variant surveillance program in wastewater serving as a benchmark for parameterization and prototype stability. The result is an integrated, end-to-end workflow that simplifies bioinformatics analysis, replacing the need for multiple manual steps and varying tool dependencies. This integrated environment enhances version control and standardization, catering to the needs of public health surveillance.

Since its introduction at the Biohackathon 2022, the finalized version of V-pipe, incorporated into V-pipe version 3.0, has been made accessible to a wider audience and has been successfully adopted by similar surveillance projects, underlining its value and effectiveness in the field [@microorganisms11112660].

## Galaxy

During the biohackathon, we engaged in productive discussions with researchers working on the Galaxy platform, exploring ways to make various analytical tools available within Galaxy's ecosystem.

Since the conclusion of the biohackathon, there have been notable advancements in the integration of wastewater analysis tools into the Galaxy platform. Notably, tools such as COJAC are now accessible via a visual, user-friendly point-and-click interface on Galaxy (accessible at COJAC on Galaxy [https://usegalaxy.eu/root?tool_id=cooc_mutbamscan](https://usegalaxy.eu/root?tool_id=cooc_mutbamscan)). This integration enhances the accessibility of these tools, providing users with a seamless experience while also enabling their incorporation into comprehensive Galaxy workflows.

# Discussion

The primary objective of this project was to identity the opportunities for standardization within the various bioinformatic methods used in WBE. Through our exploration, we have identified several crucial factors in the analysis of wastewater data, spanning from the unique characteristics of the wastewater sample to the interpretation of results, with a significant emphasis on the pivotal role played by analysis workflows and tools. To address these considerations, we have delineated two distinct stages within omic wastewater surveillance workflows and have constructed a comprehensive framework of components (such as modules and tools) that can be effectively harnessed to create end-to-end genomic wastewater surveillance pipelines. These two omic wastewater surveillance workflows can be categorized as follows:

1. Design and _in-silico_ validation of primers and benchmarking bioinformatic pipelines.
2. Application 
    1. Specific target analyses, often focused on single viruses and their variants, typically relying on tiling amplicon-based methods.
    2. Analyses of unknown targets using metagenomics and metatranscriptomics approaches.

For each of these stages, we have identified key phases, excluding the sampling and wet-lab portions of the process. In this biohackathon we have demonstrated the advantage of integrated workflows such as V-pipe and the integration of tools into the Galaxy platform. Integrated pipelines/workflows enhance efficiency, reliability, and usability in a domain often fraught with complexities associated with disparate tools and formats. Their capacity to reduce the requirement for specialized knowledge is instrumental in standardizing genomic surveillance practices within public health and scientific research.

Nonetheless, given the diverse array of tools available for processing High-Throughput Sequencing data from wastewater, even within the same phase, there is a critical need for comprehensive bioinformatic benchmarking to compare and contrast the resulting outputs. This need is further underscored by the presence of various methodologies, such as amplicon-based and metagenomics/metatranscriptomics approaches, each with their own specific set of variations from primer choice to rRNA depletion. Furthermore, the outcomes and interpretations of these bioinformatic analyses are highly contingent on the chosen workflow, spanning from the wet-lab to the bioinformatics (dry-lab) stages and the original sample. 

In conclusion, ongoing research efforts, with a specific focus on _in-silico_ validation and the practical implementation of workflows, remain essential in advancing our comprehension of viral presence and distribution within wastewater systems using bioinformatic approaches for virus surveillance.
 
## Acknowledgements

Some of the authors were funded by ELIXIR, the research infrastructure for life-science data, to join the BioHackathon Europe.

## References

