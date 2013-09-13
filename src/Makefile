all: liblbfgs-1.10  liblinear-1.93  libsvm-3.17  mallet-2.0.7  srilm-1.7.0-Lite

liblbfgs-1.10: ../download/liblbfgs-1.10.tar.gz
	tar xvzf $<
	cd $@; make

liblinear-1.93: ../download/liblinear-1.93.tar.gz
	tar xvzf $<
	cd $@; make

libsvm-3.17: ../download/libsvm-3.17.tar.gz
	tar xvzf $<
	cd $@; make

mallet-2.0.7: ../download/mallet-2.0.7.tar.gz
	tar xvzf $<
	cd $@; make

srilm-1.7.0-Lite: ../download/srilm-1.7.0-Lite.tgz
	mkdir -p $@
	cd $@; tar xvzf $<; make World
