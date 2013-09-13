DATA=../../data/review_polarity/txt_sentoken

# We use 1/5 of the data for testing 4/5 for training by taking every
# 5th file in the data as a test instance.  Try changing which 5th by
# modifying FOLD from 0 to 4.
NFOLDS=5
FOLD=0
TEST=ls ${DATA}/*/* | awk 'NR%${NFOLDS}==${FOLD}'
TRAIN=ls ${DATA}/*/* | awk 'NR%${NFOLDS}!=${FOLD}'

all: perceptron.eval

# The single argument to perceptron determines the number of passes over data
perceptron.model: perceptron
	${TRAIN} | ./perceptron 100 > perceptron.model

perceptron.test: nbtest perceptron.model
	${TEST} | ./nbtest perceptron.model > perceptron.test

perceptron.eval: nbeval perceptron.test
	${TEST} | ./nbeval perceptron.test

aperceptron.model: aperceptron
	${TRAIN} | ./aperceptron 100 > aperceptron.model

aperceptron.test: nbtest aperceptron.model
	${TEST} | ./nbtest aperceptron.model > aperceptron.test

aperceptron.eval: nbeval aperceptron.test
	${TEST} | ./nbeval aperceptron.test

# Remove all produced files
clean:
	-rm perceptron.model perceptron.test aperceptron.model aperceptron.test
