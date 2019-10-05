# Train a vector embedded model

python -m spacy init-model sv ./init_models/w2v -v ./vectors/word2vec.txt

python -m spacy pretrain sents_webbnyheter2013.jsonl ./init_models/w2v ./pretrained/w2v --n-iter 10 --use-vectors

python -m spacy train sv models_temp sv_talbanken-ud-train.json sv_talbanken-ud-dev.json -p 'tagger,parser' -t2v ./pretrained/w2v/model9.bin -n 55
