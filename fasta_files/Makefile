include ../biomakefiles/lib/make/makefile.misc

ADD_IDENTIFIER = for a in $$(cut -f 1 $< | grep -v 'accession'); do \
	    s=$$(awk -F'\t' "{ if ( \$$1 ~ /$$a/ ) { print \$$4 } }" $<); \
	    if [ "$$s" ]; then \
	    	gunzip -c links/$${a}*$(suffix $(basename $(word 2,$^))).gz | sed "/^>/s/$$/ [$$s]/" | $(CLEAN_FASTA) | gzip -c >> $@; \
	    else \
	    	echo "Couldn't find $$a in $<"; \
	    fi; \
	done

all: contigs.fna.gz orfs.ffn.gz proteins.faa.gz

contigs.fna.gz: links/metadata.tsv $(wildcard links/*.fna.gz)
	$(ADD_IDENTIFIER)

orfs.ffn.gz: links/metadata.tsv $(wildcard links/*.ffn.gz)
	$(ADD_IDENTIFIER)

proteins.faa.gz: links/metadata.tsv $(wildcard links/*.faa.gz)
	$(ADD_IDENTIFIER)
