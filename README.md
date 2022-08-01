# Quantifying Collective Identity from Self-defining Hashtags: Data and Code
Data and code accompanying article [Quantifying Collective Identity Online from Self-defining Hashtags](https://www.researchsquare.com/article/rs-960863/latest) by Alexander T. J. Barron and Johan Bollen.

Measurements and figures can be reproduced from the Jupyter notebooks and the graph edge list included.  Specific results from our analysis are saved in `.pkl` (python [pickle](https://docs.python.org/3/library/pickle.html)) or `.gt` ([graph-tool format](https://graph-tool.skewed.de/static/doc/gt_format.html)) files, which can be loaded in the notebooks.  Alternatively, slightly different results (from random variation in inference, etc.) can be created by running notebook code and saving new file versions.

Per the Twitter Developer Agreement and Policy, raw tweet and profile data is not allowed to be redistributed, but we do include a file of Twitter User IDs used in our analysis, described below.

Archived at Zenodo: [![DOI](https://zenodo.org/badge/519398822.svg)](https://zenodo.org/badge/latestdoi/519398822)

## Files

All `.gz` and `.bz2` files use level 9 compression.  See notebooks for details.

* `QuantifyingCollectiveIdentity_graph_edgelist.txt.gz`: edges and associated hashtags for the graph analyzed in the paper.
* `QuantifyingCollectiveIdentity_graph_TwitterUserIDs.txt.gz`: The 91,093 Twitter User IDs of the graph analyzed in this work, deemed to be non-bot (see paper).  Current profile data for these users may be harvested through the Twitter API.  Markers for the giant component of the graph and its 2-core are included, but vertices are not tied to specific Twitter IDs.
* `QuantifyingCollectiveIdentity_2core_Louvainpartitiondendrogram.pkl`: Louvain hierarchy fit presented in the paper.
* `Louvain_hashtagimportanceout_1stlvl.pkl`: Hashtag importance scores for the Louvain first-level partition.
* `Louvain_1stlvl_binary_comm_mutinf.pkl`: Coherence scores measured for the Louvain hierarchy.
* `QuantifyingCollectiveIdentity_nullconspicuousness_precalc.pkl`: Pre-calculated null Louvain conspicuousness scores, used as a notebook example.
* `Ggiant_2core_GT.gt.xz`: graph-tool representation of the 2-core.
* `Ggiant_2core_nx-to-gt_vtxconvdict.pkl'`: Mapping of vertices from original networkx graph to graph-tool graph.
* `Ggiant_2core_NestedBlockState.pkl.gz`: Hierarchical Stochastic Block Model (SBM) inferred from the 2-core and used in our analysis.
* `statsperlevel_SBM.pkl`: Comparison table between clustering levels of the SBM and Louvain hierarchies.
* `SBM_labelimportanceout_perlevel.pkl`: Hashtag importance scores for multiple levels of the SBM partition hierarchy.
* `SBM_binarycommprobs_bottomlevels.pkl`: Binary cluster probabilities used to calculate coherence for different bottom-levels of the SBM hierarchy, with respect to the designated top level (see paper).
* `SBM_levelcompcondprobs_bottomlevels.pkl`: Conditional top-level SBM cluster probabilities given clusters at different bottom-levels (see paper).
* `SBMlevel_Louvain_optimalclusterassignments.pkl`: Optimal cluster matching assignments between clusters at each SBM level and Louvain bottom-level clusters.  Clustering is determined by maximizing overall matched cluster overlap score (see notebooks).
* `SBM_agglvl_binary_hashtag_pdistsplits_dict.pkl.bz2`: Label vocabulary probability distributions for clusters vs. their complements at every SBM level.  Generated in notebook code and used to calculate conspicuousness via Jensen-Shannon Divergence.
* `QuantifyingCollectiveIdentity_nullconspicuousness_SBM_precalc.pkl`: Pre-calculated null SBM conspicuousness scores, used as a notebook example.

## Notebooks

* `Quantifying_Collective_Identity_from_Self-defining_Hashtags_Louvain.ipynb`: Louvain analysis code.
* `Quantifying_Collective_Identity_from_Self-defining_Hashtags_StochBlockModel_comparison.ipynb`: Code comparing hierarchical SBM results to Louvain results.

## Script requirements (versions used)

* python (3.10.4)
* [powerlaw](https://github.com/jeffalstott/powerlaw) (1.5)
* [python-louvain](https://github.com/taynaud/python-louvain) (0.16)
* [graph-tool](https://graph-tool.skewed.de/) (2.44 (commit 7edcecc2, Wed Jan 12 10:59:17 2022 -0500))
* igraph (0.9.10)
* networkx (2.8)
* pandas (1.4.2)
* matplotlib (3.5.2)
* numpy (1.22.3)
* scipy (1.8.0)
