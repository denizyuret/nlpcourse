DATA=../../data/review_polarity/txt_sentoken
NFOLDS=5
FOLD=0
TEST=ls ${DATA}/*/* | awk 'NR%${NFOLDS}==${FOLD}'
TRAIN=ls ${DATA}/*/* | awk 'NR%${NFOLDS}!=${FOLD}'
NGRAM=4
VOCAB=10

all: srilm.eval

vocab.gz: ${DATA}
	cat `ls ${DATA}/*/*` | ngram-count -text - -write-order 1 -write - | awk '$$2>${VOCAB}' | cut -f1 | gzip > $@

pos.lm.gz: ${DATA} vocab.gz
	cat `${TRAIN} | grep /pos/` |\
	ngram-count -order ${NGRAM} -kndiscount -interpolate -unk -vocab vocab.gz -text - -lm pos.lm.gz

neg.lm.gz: ${DATA} vocab.gz
	cat `${TRAIN} | grep /neg/` |\
	ngram-count -order ${NGRAM} -kndiscount -interpolate -unk -vocab vocab.gz -text - -lm neg.lm.gz

srilm.test: lmtest pos.lm.gz neg.lm.gz
	${TEST} | ./lmtest > srilm.test

srilm.eval: nbeval srilm.test
	${TEST} | ./nbeval srilm.test

# Remove all produced files
clean:
	-rm -rf vocab.gz pos.lm.gz neg.lm.gz srilm.test
