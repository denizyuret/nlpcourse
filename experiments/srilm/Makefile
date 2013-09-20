BROWN=../../download/treebank3-tagged-pos-brown.tok.gz
WSJ=../../download/treebank3-parsed-mrg-wsj.tok.gz
#NGRAM_OPTIONS=-order 3 -unk -lm foo.lm -ppl foo.txt -debug 2
#NGRAM_COUNT_OPTIONS=-order 5 -kndiscount -interpolate -write-binary-lm -unk -vocab wsj.vocab -text foo.txt -lm foo.lm

all:

# Experiment 1: compare wsj-train brown-test and brown-train wsj-test.
# Understand the difference between ppl and ppl1

wsj-brown01: ${WSJ} ${BROWN}
	ngram-count -text ${WSJ} -lm - | \
	ngram -lm - -ppl ${BROWN}

brown-wsj01: ${BROWN} ${WSJ}
	ngram-count -text ${BROWN} -lm - | \
	ngram -lm - -ppl ${WSJ}

# Use -debug 2 and calculate ppl, ppl1 from individual words
# Note that unknown words are simply skipped

wsj-brown02: ${WSJ} ${BROWN}
	ngram-count -text ${WSJ} -lm - | \
	ngram -lm - -ppl ${BROWN} -debug 2 | \
	./debug2stats

brown-wsj02: ${BROWN} ${WSJ}
	ngram-count -text ${BROWN} -lm - | \
	ngram -lm - -ppl ${WSJ} -debug 2 | \
	./debug2stats
