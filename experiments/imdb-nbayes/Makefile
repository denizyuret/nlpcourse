DATA=../../data/review_polarity/txt_sentoken
NFOLDS=5
FOLD=0
TEST=ls ${DATA}/*/* | awk 'NR%${NFOLDS}==${FOLD}'
TRAIN=ls ${DATA}/*/* | awk 'NR%${NFOLDS}!=${FOLD}'

all: nbayes.eval

nbayes.model: nbayes
	${TRAIN} | ./nbayes 1.0 > nbayes.model

nbayes.test: nbtest nbayes.model
	${TEST} | ./nbtest nbayes.model > nbayes.test

nbayes.eval: nbeval nbayes.test
	${TEST} | ./nbeval nbayes.test

# Remove all produced files
clean:
	-rm nbayes.model nbayes.test
