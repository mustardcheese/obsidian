EDA -- exploratory data analysis
	make sure we know what's in our data before we train

## Unsupervised + Supervised Learning

![[Pasted image 20260518104713.png|600]]
$X_{n \times d}$ -> dataset or data point matrix
$Y_{n \times 1}$ -> labels or target values
* cat, dog, etc. are discrete labels
* numbers would be concrete labels
* binary problem with just 2 labels

Each row $n$, aka point, item, instance, example, data point
* We want **more** data points, **more** rows

Each col $d$, aka dimension, feature, attribute, variable
* We **don't want more** features, unless we have adequate data

**Unsupervised** means only focusing on $X$
**Supervised** means focusing on $X$ and $Y$

Why do we drop Y sometimes?
* **Labels/labeling are expensive**
- It is a very difficult task to label data, or get $Y$
Then how can we just use X?
- We can cluster information together
- Cats other cats tend to have similar attributes

### Notation
Training Data:
	$X_{n \times d} \rightarrow \text{datapoints}$ 
	$Y_{n \times 1}$

Subscript means feature (column)
	$x_\textbf{1} \rightarrow \text{feature 1}$
	$x_\textbf{2} \rightarrow \text{feature 2}$
	$x_\textbf{n} \rightarrow \text{feature n}$

Superscript means data point (row)
	$x^{[1]} \rightarrow \text{data point 1}$
	$x^{[2]} \rightarrow \text{data point 2}$
	$x^{[n]} \rightarrow \text{data point n}$

$X_{n \times d}$
	$\text{data points} \times \text{features}$

## Dimensionality Reduction
