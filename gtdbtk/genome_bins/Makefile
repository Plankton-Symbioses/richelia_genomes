all_fna: $(subst .fna.gz,.fna,$(wildcard *.fna.gz))

%.fna: %.fna.gz
	gunzip -c $< > $@
