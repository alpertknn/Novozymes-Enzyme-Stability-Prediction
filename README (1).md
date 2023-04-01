
# Novozymes Enzyme Stability Prediction


Enzymes are proteins that act as catalysts in the chemical reactions of living organisms. The goal of this competition is to predict the thermostability of enzyme variants. The experimentally measured thermostability (melting temperature) data includes natural sequences, as well as engineered sequences with single or multiple mutations upon the natural sequences. 

Understanding and accurately predict protein stability is a fundamental problem in biotechnology. Its applications include enzyme engineering for addressing the world’s challenges in sustainability, carbon neutrality and more. Improvements to enzyme stability could lower costs and increase the speed scientists can iterate on concepts.



## Attribute Information
The training set, the protein thermostability (experimental melting temperature) data includes natural sequences, as well as engineered sequences with single or multiple mutations upon the natural sequences. The data are mainly from different sources of published studies such as Meltome atlas—thermal proteome stability across the tree of life.

- seq_id: unique identifier of each protein variants
- protein_sequence: amino acid sequence of each protein variant. The stability (as measured by tm) of protein is determined by its protein sequence. (Please note that most of the sequences in the test data have the same length of 221 amino acids, but some of them have 220 because of amino acid deletion.)
- pH: the scale used to specify the acidity of an aqueous solution under which the stability of protein was measured. Stability of the same protein can change at different pH levels.
- data_source: source where the data was published
- tm: target column. Since only the spearman correlation will be used for the evaluation, the correct prediction of the relative order is more important than the absolute tm values. (Higher tm means the protein variant is more stable.)

The test set contains experimental melting temperature of over 2,413 single-mutation variant of an enzyme (GenBank: KOC15878.1), obtained by Novozymes A/S.

There are also other publicly available methods which can predict protein stabilities such as ESM, EVE and Rosetta etc., without using the provided training set.

Submissions are evaluated on the Spearman's correlation coefficient between the ground truth and the predictions.. Since it will be a kaggle submission, the output should be;



## Sample Output

```javascript
seq_id , tm
31394 ,  9.7
31395 ,  56.3
31396 , 112.4
etc.
```


## Acquirements

Outliers and NULL values were checked, only "bmi" column had some NULL values and they were dropped. Variables and their relationships, and correlations were inspected with different plots. In previous versions of work, the RandomForestClassifier was used as an algorithm. However, StratifiedKFold gave better results than RandomForestClassifier. Therefore, StratifiedKFold used and tuned.

Here are the steps that are taken in this analysis period:

- Reading Related Files
- Controlling Variables whether They Contain Null or Not
- Merging Train and Original Dataset
- Separating Numericals and Categoricals In Order to Visualise
- Interpretting the Variables with Describe Method
- Plotting Sides
- Model Creation and Separation of Dependent/Independent Variables
- Model Parameter Tuning
- Inspection Variable Importances 
- Submission of File



