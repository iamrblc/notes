# Notes
Módosítani kéne a flowt úgy, hogy 
1. Feldarabolni 5 mp-es szakaszokra
2. 5 mp-s szakaszokat embeddelni
3. embeddingeken logisztikus regresszió.
4. ahol esélyes volt, hogy van valami:
	1. összegyúrni egybe (ha két egymást követő szakasz mind threshold fölötti)
	2. hozzáadni 1-2 másodpercet az elejére és a végére (hogy attackot, releaset is találjon)
	3. feldarabolni csak a candidate részeket 1 mp-es szakaszokra 0.2 mp-es csúszóablakkal
	4. paddelni ezeket a kis szegmenseket
	5. embeddelni őket
	6. logisztikus regresszió
	7. ez alapján megcisnálni a heatmapet.


# Model 0 

## Set:
360 positive (dog), 360 negative samples (no dog)
six environments (silence, pink noise, plaza, home, zoo, street): 60-60 each 

## Pipeline

1. Standard scaling: normalize fatures to zero mean, unit variance
2. Logistic regression
	1. Ridge (l2) penalty: we have multiple features. Works better than Lasso. Shrinks weights smoothly. More stable, no sparsity.
	2. Regularization strenght (C): 0.1 - Pretty low, for strong regularization. 
	3. Maximum iteration: 1000 - ensures slower convergence
	4. Random seed is 42. It is set in the config. 

```python
make_pipeline(
	StandardScaler(),
	LogisticRegression(
		penalty='l2',
		C=0.1,
		max_iter=1000,
		random_state=seed)
)
```

These params can probably stay even for larger datasets. But we'll see if C needs to be increased or decreased if new training underfit/overfit. 

## CV:
Fold 1/5: Accuracy: 0.9792 F1 (weighted): 0.9792 Per-class F1: no_dog=0.980, dog=0.979
Fold 2/5: Accuracy: 0.9722 F1 (weighted): 0.9722 Per-class F1: no_dog=0.972, dog=0.972
Fold 3/5: Accuracy: 0.9861 F1 (weighted): 0.9861 Per-class F1: no_dog=0.986, dog=0.986
Fold 4/5: Accuracy: 0.9861 F1 (weighted): 0.9861 Per-class F1: no_dog=0.986, dog=0.986
Fold 5/5: Accuracy: 0.9514 F1 (weighted): 0.9513 Per-class F1: no_dog=0.954, dog=0.949

