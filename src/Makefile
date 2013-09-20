all:

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

srilm-1.7.0: ../download/srilm-1.7.0.tgz
	mkdir -p $@
	cd $@; tar xvzf ../$<; make World
	# If this fails the first time read INSTALL and edit the Makefile 

wasp-1.0: ../download/wasp-1.0.tar.gz
	tar xvzf $<

wasp-2.0alpha: ../download/wasp-2.0alpha.tar.gz
	tar xvzf $<
