assemblies.accnos: bac120_metadata_r202.tsv
	awk '{ if ( $$18 ~ /Richelia/ || $$18 ~ /Calothrix_A/ ) { print substr($$1, 4) "\t" $$18 } }' $< > $@

copy: assemblies.accnos
	for a in $$(cut -f 1 $<); do \
	    if [ -e /data/gtdb/genomes/$${a}*fna.gz ]; then \
	        cp /data/gtdb/genomes/$${a}*fna.gz .; \
		cp -r /data/gtdb/genomes/$${a}*prokka.d .; \
	    else \
		echo "Can't find /data/gtdb/genomes/$${a}*fna.gz"; \
	    fi; \
	done
	touch $@
