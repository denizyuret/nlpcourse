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

# Experiment 3: Add the -unk option to both ngram-count (which puts it
# into the model) and ngram (which expects it but does not change its
# behaviour other than suppressing a warning.)

wsj-brown03: ${WSJ} ${BROWN}
	ngram-count -unk -text ${WSJ} -lm - | \
	ngram -unk -lm - -ppl ${BROWN}

brown-wsj03: ${BROWN} ${WSJ}
	ngram-count -unk -text ${BROWN} -lm - | \
	ngram -unk -lm - -ppl ${WSJ}

# Experiment 4: Fixed vocabulary.  How to choose the vocabulary?  Is
# this a fair comparison.  What would happen with an empty vocabulary
# model file (all words would get probability ~ 1!

# Experiment 5: Create a word model or explode unknown words (optional).

# Experiment 6: Cross validation (or bootstrap) and measuring standard
# error and generating a learning curve.

# IDEAS: can also vary ngram order, discount method, vocab size?, word
# split etc.
# IDEAS: ngram -gen generates random sentences!
# IDEAS: bootstrap to handle experimental uncertainty (both train and
# test set?)
# IDEAS: learning curve and the effect of data size, combine with bootstrap.

# Only pick stuff that will be useful in the future:
# Max Likelihood and overfitting. (can be implemented as absolute
# discounting with 0 discount parameter?)
# Discounting and smoothing, i.e. regularization
# Picking the regularization parameter from a validation set.
# Train/test split, effect of domain difference?
# Standard error of results and significance of differences.
# Learning curve analysis.

# Check out http://www2.denizyuret.com/ref/jurafsky/224s.07.lec11.6up.pdf


wsj.lm.gz: ${WSJ}
	ngram-count -text ${WSJ} -lm $@

clean:
	rm wsj.lm.gz
