# But what does the dog say?

## Intro

- we DO know what dogs say (slide with vocal repertoire map).
- they are good in interspecific cooperative communication with us. so many of these we recognize.
- in fact, very recently we published a paper that dives deep into why what they say is not like human speech 
- what we don't know, a seemingly tiny but crucial detail, if what they say is malleable by external examples. in other words, if they are capable of vocal learning. 
- ERC Consolidator Grant funded BARKS Lab within the Department of Ethology
- We approach this from various angles. 

## The Lab's subgroups slide
- behavior
- bioacoustics
- neuro
- ml
I work in the last two as Data Scientist, and here I'm talking about the machine learning aspect of this work.

## WHY MACHINE LEARNING?
- manual labelling / analysis sucks
- a bit of history/tradition (our department came out with a simple classification in 2008)

## AUDIO DATA
- the department of ethology has 20 yrs of recordings, contextually labelled
- new collections from the audio lab
- 13000 annotated segments (heavily biased, barks, growls, whines)

## DESIRES
- call classification
- context recognition
- well annotated dataset
(This is a bit of a chicken or egg problem. So we'll approach it similarly using a semi-supervised learning. Also, there are some annotated datasets, but they are meh.)

## WHY NOT OFF THE SHELF MODELS?

- specific to our needs:
	- morphological variance
	- environmental variance (indoors, outdoors, lab, rural, city, humans talking in the background, etc)
	- heavy class imbalance
	- technical parameters (recording devices, formats, sampling rates - esp. in the future with citizen science)
	You certainly cannot address everything at once, but you need to think flexibly and have your data engineering plans accordingly when you put together your pipeline. The pipeline has to be flexible not only to address future issues, but because the development of the model requires lots of iterations. 
- many are heavily context dependent
- big data overkill
	- some benchmarking results from Mohab's thesis (Resnet generalizes worse under certain tasks)

## Let's see an example. 
You store your raw data. Tabular structures will soon run out due to poor scalablility.
- hdf5. why? flexible, scalable, RAM friendly which is a great adventage, if you don't start your prototyping right on an HPC. 
- Here i'll show the architecture of my h5 file. 
- Allows you to create test-train separation based on indices. 
- preprocessing (what's the adventage here?)
- self contain data and model parameters (is this generally true? I did this. i mean does this provide an edge?)
- allows for in-line (during training) augmentation. 

But does it work?
Funny story: my student's computer broke just before submission deadline. So we put all his models in the pipeline. And yes. 

## We ran the classification tests on a limited dataset.
But could we save time from finding potentially interesting bits from long audio and then classify them?

This is a big jump. The idea: build a sound event detector: 