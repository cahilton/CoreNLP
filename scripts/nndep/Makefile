ENGLISH_EMBEDDINGS=/u/nlp/data/depparser/nn/data/embeddings/en-cw.txt
CHINESE_EMBEDDINGS=/u/nlp/data/depparser/nn/data/embeddings/zh-word2vec.txt

DATA_DIR=/u/nlp/data/dependency_treebanks

PTB_STANFORD_TRAIN=${DATA_DIR}/PTB/Stanford_3_3_0/train.conll
PTB_STANFORD_DEV=${DATA_DIR}/PTB/Stanford_3_3_0/dev.conll
PTB_STANFORD_TEST=${DATA_DIR}/PTB/Stanford_3_3_0/test.conll

PTB_CONLL_TRAIN=${DATA_DIR}/PTB/CoNLL/train.conll
PTB_CONLL_DEV=${DATA_DIR}/PTB/CoNLL/dev.conll
PTB_CONLL_TEST=${DATA_DIR}/PTB/CoNLL/test.conll

CTB_CONLL_TRAIN=${DATA_DIR}/CTB/train.gold.conll
CTB_CONLL_DEV=${DATA_DIR}/CTB/dev.gold.conll
CTB_CONLL_TEST=${DATA_DIR}/CTB/test.gold.conll

UD_GERMAN_TRAIN=${DATA_DIR}/UD/1.1/de/de-ud-train-clean.conllu
UD_GERMAN_DEV=${DATA_DIR}/UD/1.1/de/de-ud-dev-clean.conllu
UD_GERMAN_TEST=${DATA_DIR}/UD/1.1/de/de-ud-test-clean.conllu


UD_FRENCH_TRAIN=${DATA_DIR}/UD/1.1/fr/fr-ud-train-clean.conllu
UD_FRENCH_DEV=${DATA_DIR}/UD/1.1/fr/fr-ud-dev-clean.conllu
UD_FRENCH_TEST=${DATA_DIR}/UD/1.1/fr/fr-ud-test-clean.conllu


PTB_Stanford:
	java edu.stanford.nlp.parser.nndep.DependencyParser -props nndep.properties -trainFile $(PTB_STANFORD_TRAIN) -devFile $(PTB_STANFORD_DEV) -embedFile $(ENGLISH_EMBEDDINGS) -model $@.txt.gz > $@.log 2>&1
	@echo "\nBeginning evaluation (dev set).." >> $@.log
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(PTB_STANFORD_DEV) -model $@.txt.gz -outFile $@.out.dev >> $@.log 2>&1
	@echo "\nBeginning evaluation (test set).." >> $@.log
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(PTB_STANFORD_TEST) -model $@.txt.gz -outFile $@.out.test >> $@.log 2>&1

PTB_CoNLL:
	java edu.stanford.nlp.parser.nndep.DependencyParser -props nndep.properties -trainFile $(PTB_CONLL_TRAIN) -devFile $(PTB_CONLL_DEV) -embedFile $(ENGLISH_EMBEDDINGS) -model $@.txt.gz >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(PTB_CONLL_DEV) -model $@.txt.gz -outFile $@.out.dev >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(PTB_CONLL_TEST) -model $@.txt.gz -outFile $@.out.test >> $@.log 2>&1

CTB_CoNLL:
	java edu.stanford.nlp.parser.nndep.DependencyParser -props nndep.properties -trainFile $(CTB_CONLL_TRAIN) -language Chinese -devFile $(CTB_CONLL_DEV) -embedFile $(CHINESE_EMBEDDINGS) -model $@.txt.gz >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(CTB_CONLL_DEV) -language Chinese -model $@.txt.gz -outFile $@.out.dev >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(CTB_CONLL_TEST) -language Chinese -model $@.txt.gz -outFile $@.out.test >> $@.log 2>&1

UD_GERMAN:
	java edu.stanford.nlp.parser.nndep.DependencyParser -props nndep.properties -trainFile $(UD_GERMAN_TRAIN) -language German -devFile $(UD_GERMAN_DEV) -model $@.txt.gz >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(UD_GERMAN_DEV) -language German -model $@.txt.gz -outFile $@.out.dev >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(UD_GERMAN_TEST) -language German -model $@.txt.gz -outFile $@.out.test >> $@.log 2>&1

UD_FRENCH:
	java edu.stanford.nlp.parser.nndep.DependencyParser -props nndep.properties -trainFile $(UD_FRENCH_TRAIN) -language German -devFile $(UD_FRENCH_DEV) -model $@.txt.gz >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(UD_FRENCH_DEV) -language French -model $@.txt.gz -outFile $@.out.dev >> $@.log 2>&1
	java edu.stanford.nlp.parser.nndep.DependencyParser -testFile $(UD_FRENCH_TEST) -language French -model $@.txt.gz -outFile $@.out.test >> $@.log 2>&1

