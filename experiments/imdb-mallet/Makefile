DATA=../../data/review_polarity/txt_sentoken

all:
	@echo Use Method.eval to run mallet on imdb movie review polarity data
	@echo where Method can be some of: AdaBoostM2 AdaBoost Bagging
	@echo BalancedWinnow C45 ClassifierEnsemble Classifier
	@echo ConfidencePredictingClassifier DecisionTree
	@echo FeatureSelectingClassifier MaxEntGERange MaxEntGE MaxEntL1 MaxEntPR
	@echo MaxEnt MCMaxEnt NaiveBayesEM NaiveBayes RankMaxEnt Winnow
	@echo See http://mallet.cs.umass.edu/api/cc/mallet/classify/package-summary.html

%.eval:
	mallet import-dir --input ${DATA}/* --output - |\
	mallet train-classifier --trainer $* --cross-validation 5 --input -
