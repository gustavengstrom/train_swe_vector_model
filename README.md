# Train a Swedish vector embedded model

The following is a scaled down minimimal working example of what is intended to produce a Swedish language model in spacy with word vectors embedded. Word vector file and pretrain examples have been reduced in order to allow for easy testing
of error. 

The last line of the following code generates the following error:

>> ValueError: cannot reshape array of size 110592 into shape (96,3,480)

To replicate the error it should be enough to git clone the repository and run the following lines of code:

python -m spacy init-model sv ./init_models/ -v word2vec.txt

python -m spacy pretrain sents_webbnyheter2013.jsonl ./init_models ./pretrained --n-iter 10 --use-vectors

python -m spacy train sv models_temp sv_talbanken-ud-train.json sv_talbanken-ud-dev.json -p 'tagger,parser' -t2v ./pretrained/model9.bin -n 10
