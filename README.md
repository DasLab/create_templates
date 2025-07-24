# create_templates
Create 3D templates (or solution) file for RNA.

Currently based on MMseqs to carry out search and alignment.

See also [MMseqs2 3D RNA Template notebook](https://www.kaggle.com/code/rhijudas/mmseqs2-3d-rna-template-identification) on Kaggle, which has the full workflow! 

Requirements: `biopython`.


## Example command line

```
cd example/
python3 ../create_templates_csv.py \
	 -s validation_sequences.csv \
	--mmseqs_results_file validation_Result.txt \
	--skip_temporal_cutoff \
	-o validation_templates.csv 
```

Output should match what is in `example/output/validation_templates.csv`

## How to run MMseqs2

To get the mmseqs file, install [MMseqs2](https://github.com/soedinglab/MMseqs2), and within `example/`, use command lines like

```
mmseqs createdb ../PDB_RNA/pdb_seqres_NA.fasta pdb_seqres_NA  --dbtype 2
mmseqs easy-search validation_sequences.fasta pdb_seqres_NA  validation_Result.txt tmp --search-type 3 --format-output "query,target,evalue,qstart,qend,tstart,tend,qaln,taln"
```




