# Co-expression-analysis-using-Camoco
Co-expression analysis using Camoco

Camoco(Schaefer et al., 2018) was used to prioritize causal RSA-related genes in maize. The GWAS locus information was derived from the genome-wide association analysis, and density metrics were used to perform the co-expression network analysis. The candidate window size was 50 kb, and the maximum number of flanking genes was two. The candidate windows were calculated both upstream and downstream of the input SNPs. 

#Building RefGen Object

$ camoco build-refgen \
 ZmB73_5b_FGS.gff \
 "Zm5bFGS"  \
 "Maize 5b Filtered Gene Set" \
 5b \
 "Zea mays"


#Building COB object (co-expression network)

$ camoco build-cob \
  Root_FPKM_35lines.txt \
  ZmRoot_35lines \
  "Maize Root Network 19CA_HN35lines" \
  Zm5bFGS


#Building Ontology Datasets

$ camoco build-go \
  zm_go.tsv \
  go.obo \
  "ZmGO" \
  "Maize GO" \
  Zm5bFGS
  
  
#Building GWAS Object

$ camoco build-gwas \
 ZmRoot20_merge8traits.allLocs.csv \
 ZmRoot20CMLM_8traits \
 "Maize Root 0-20 GWAS" \
 Zm5bFGS \
 --sep ',' \
 --trait-col \
 roottraits \
 --chrom-col chr \
 --pos-col pos


#Calculating co-expression

$ camoco overlap \
 ZmRoot_35lines \
 density \
 --gwas ZmRoot0CMLM_8traits \
 --term merge8traits \
 --candidate-window-size 50000 \
 --candidate-flank-limit 2





Reference

Schaefer, R.J. et al. Integrating coexpression networks with gwas to prioritize causal genes in maize. Plant Cell 30, 2922-2942 (2018).
