DATA=../../data/review_polarity/txt_sentoken
NFOLDS=5
FOLD=0
TEST=ls ${DATA}/*/* | awk 'NR%${NFOLDS}==${FOLD}'
TRAIN=ls ${DATA}/*/* | awk 'NR%${NFOLDS}!=${FOLD}'

all: logistic.eval svm.eval

svm.data: svmdata
	ls ${DATA}/*/* | svmdata > svm.data

svm.eval: svm.data
	train -s 1 -c 1e-3 -v 5 svm.data

logistic.eval: svm.data
	train -s 0 -c 1 -v 5 svm.data

# Remove all produced files
clean:
	-rm -rf svm.data
