DATA=../../data/review_polarity/txt_sentoken

all: loglinear.eval

# Extract the most frequent N words from the data
vocab.dat: vocab
	cat ${DATA}/*/* | ./vocab 1000 > vocab.dat

# Convert each file to a single line with class and features
# Class obtained from path (pos/neg)
# Words that are not in vocab are replaced with the <unk> token
feats.dat: feats vocab.dat
	ls ${DATA}/*/* | ./feats vocab.dat > feats.dat

# Train with 4/5 of the data, test with the other 1/5
TRAIN=awk 'NR%5!=0' feats.dat
TEST =awk 'NR%5==0' feats.dat

# LogLinear

loglinear.model: loglinear vocab.dat feats.dat
	${TRAIN} | ./loglinear vocab.dat > loglinear.model

loglinear.test: logltest loglinear.model feats.dat
	${TEST} | cut -d' ' -f 2- | ./logltest loglinear.model > loglinear.test

loglinear.eval: eval loglinear.test feats.dat
	${TEST} | ./eval loglinear.test

# Remove all produced files
clean:
	-rm vocab.dat feats.dat loglinear.model loglinear.test
