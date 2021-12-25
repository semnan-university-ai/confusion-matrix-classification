# confusion-matrix-classification
Calculate Precision &amp; Recall &amp; F-Measure with Confusion Matrix (TP, TN, FP, FN)


**Confusion Matrix ::**

|  | Positive Prediction | Negative Prediction |
| - | ------------------- | -------------------- |
| Positive Class | True Positive (TP) | False Negative (FN) |
| Negative Class | False Positive (FP) | True Negative (TN) |

**Precision quantifies Formula :**

```
Precision = TruePositives / (TruePositives + FalsePositives)
Precision = TP / ( TP + FP )
```

**Recall quantifies Formula :**
```
Recall = TruePositives / (TruePositives + FalseNegatives)
Recall = TP / ( TP + FN )
```

**F-Measure quantifies Formula :**
```
F-Measure = (2 * Precision * Recall) / (Precision + Recall)
```

**Accuracy quantifies Formula :**
```
accuracy = (TruePositives + TrueNegative) / (TruePositives + FalsePositive + False Negative + TrueNegative)
accuracy = (TP + TN) / (TP + FP + FN + TN)
```

**Code (python class) :**
```
class confusionMatrixClassification:
	
	# Author : Amir Shokri
	# Email : amirsh.nll@gmail.com
	# Date : Dec 2021
	# git : https://github.com/amirshnll/confusion-matrix-classification/

	def __init__(self):
		self.tp = 0.0
		self.tf = 0.0
		self.fp = 0.0
		self.fn = 0.0

	def setTP(self, tp):
		self.tp = float(tp)

	def getTP(self):
		return float(self.tp)

	def setTF(self, tf):
		self.tf = float(tf)

	def getTF(self):
		return float(self.tf)

	def setFP(self, fp):
		self.fp = float(fp)

	def getFP(self):
		return float(self.fp)

	def setFN(self, fn):
		self.fn = float(fn)

	def getFN(self):
		return float(self.fn)

	def precision(self):
		try:
			return ( self.getTP() + self.getTF() ) / ( self.getTP() + self.getTF() + self.getFP() + self.getFN() )
		except:
			return -1 # error
			
	def accuracy(self):
		try:
			return self.getTP() / ( self.getTP() + self.getFP() )
		except:
			return -1 # error

	def recall(self):
		try:	
			return self.getTP() / ( self.getTP() + self.getFN() )
		except:
			return -1 # error
		
	def fmeasure(self):
		precision_value = self.precision()
		recall_value = self.recall()

		if precision_value == -1 or recall_value == -1:
			return -1 # error
		
		try:
			return ( 2 * precision_value ) / ( precision_value + recall_value )
		except:
			return -1 # error
```

**Code (usage) :**

```
cmc = confusionMatrixClassification()
cmc.setTP(90)
cmc.setFP(30)
cmc.setFN(10)

print("Accuracy : " + str(cmc.accuracy())) # 0.75
print("Precision : " + str(cmc.precision())) # 0.6923076923076923
print("Recall : " + str(cmc.recall())) # 0.9
print("F-Measure : " + str(cmc.fmeasure())) # 0.8695652173913042
```
