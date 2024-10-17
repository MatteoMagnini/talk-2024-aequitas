 
+++

title = "Enforcing Fairness via Constraint Injection with FaUCI"
description = "Enforcing Fairness via Constraint Injection with FaUCI"
outputs = ["Reveal"]
aliases = [
    "/guide/"
]

+++

{{% slide preload=true background-iframe="logo.html" transition="zoom" %}}

# Enforcing Fairness via Constraint Injection with FaUCI
**2nd Aequitas Workshop on Fairness and Bias in AI at ECAI 2024**

🎤 *Matteo Magnini*, **Giovanni Ciatto**, **Roberta Calegari**, **Andrea Omicini**

📧 [matteo.magnini@unibo.it](mailto:gianluca.aguzzi@unibo.it)

{{< image height="5" src="/aequitas-logo.svg" >}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Context {.highlight}
### What do we mean by fairness? {.accent}

Fairness has different meanings to us depending on our *personal background*.

{{% row %}}
{{% fragment class="col" %}}

{{< image height="30" src="/woman-judge-balance-law.svg" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{< image height="30" src="/businessman-money.svg" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{< image height="30" src="/technologist-technology.svg" >}}

{{% /fragment %}}
{{% /row %}}

{{% row %}}
{{% fragment class="col" %}}
For people with predominantly scientific studies, fairness is something that should be **objectively measurable**.
This is usually translated into the *fulfillment* of one or multiple fairness **metrics**.
{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Context {.highlight}
### Enforcing Fairness in ML models {.accent}
{{% row %}}
{{% fragment class="col" style="flex: 0 0 33%;"%}} 
#### Pre-processing

{{< image height="45" src="/data-preprocessing-vert.png" >}}

Methods that operate at **dataset level** to remove biases for sensitive groups.

{{% /fragment %}}

{{% fragment class="col" %}} 
#### In-processing

{{< image height="45" src="/in-processing-vert.png" >}}

The **training of the model** takes into account the fairness constraints.

{{% /fragment %}}

{{% fragment class="col" %}} 
#### Post-processing

{{< image height="45" src="/post-processing-vert.png" >}}

The model is treated as a black-box and only the **predictions are adjusted** to ensure fairness.

{{% /fragment %}}

{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Context {.highlight}
### The in-processing techniques {.accent}

{{% row %}}
{{% fragment class="col" %}}
#### Penalty function

A function, usually derived from a fairness metric, is chosen to *measure a violation* of fairness/bias.
This function takes into account the **input data** and the **model's predictions**.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Function computation

Because fairness metrics require **statistical distributions** to be computed, these distributions are *estimated on a subset (batch) of the data*. 
The actual computation of the fairness metric is therefore done during the loss computation.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Training

The loss function is a *combination* of the model's loss (e.g., binary cross entropy) and the fairness penalty.
it is common to use a hyperparameter to balance the two terms.

{{% /fragment %}}
{{% /row %}}


---
    
{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Open challenges {.highlight}
### Types of protected attributes {.accent}

{{% row %}}
{{% fragment class="col" %}}
#### Binary

{{< image height="20" src="/binary-data.svg" >}}

It is the **simplest case**, where the protected attribute can take only two values.
There are only two groups to be considered, the classic example is the gender.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Categorical

{{< image height="20" src="/categorical-data.svg" >}}

The protected attribute can take more than two values.
Here things start to get tricky, as we might **consider all the groups for fairness**.
Examples are ethnicity, education, and occupation.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Continuous

{{< image height="20" src="/continuous-data.svg" >}}

The protected attribute is a continuous variable.
This is the *most complex case*, as we need to **estimate probability densities** to compute fairness metrics.
An example is the income.


{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Open challenges {.highlight}
### Fairness metrics {.accent}

{{% row %}}
{{% fragment class="col" %}}
#### Group vs. Individual fairness

Group fairness is about **treating groups equally**, while individual fairness is about **treating similar individuals equally**.

Individual fairness metrics are more *computationally expensive* and because of that less common in practice.

However, also group fairness metrics can be computationally expensive.
For this reason, we decided to focus on group fairness metrics.

{{% /fragment %}}
{{% fragment class="col" %}}

- *Demographic/statistical parity* how much model's predictions are **independent** of the protected attribute.
<small>$$DP_{h, A}(X) = \sum_{a \in A} \left\|\left\| E[h(X) \mid A{=}a] - E[h(X)] \right\|\right\|$$</small>
- *Disparate impact* how much the model **disproportionately** affects a group.
<small>$$DI_{h, A}(X) = \min\left(\frac{E[h(X) \mid A{=}1]}{E[h(X) \mid A{=}0]},\frac{E[h(X) \mid A{=}0]}{E[h(X) \mid A{=}1]}\right)$$</small>
- *Equalized odds* how much the model **equally predicts** a given output for all the groups.
<small>$$EO_{h, A}(X) = \sum_{(a, y)}^{A \times Y} eo_{h, A}(X, a, y)$$</small>
<small>$$eo_{h, A}(X, a, y) = \left\|\left\| E[h(X) \mid A{=}a, Y{=}y] - E[h(X) \mid Y{=}y] \right\|\right\|$$</small>

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Fairness under Constraints Injection {.accent}

{{% row %}}
{{% fragment class="col" %}}
We design FaUCI in order to be *agnostic* to the fairness metric used and to the protected attribute type:
- we considered **demographic parity**, **disparate impact**, and **equalized odds** (any other metric can be used)
- we generalized the metric to work with **binary**, **categorical**, and **continuous** protected attributes
- we also considered ad-hoc weights for the groups to cover *corner cases* (e.g., strong imbalance)
{{% /fragment %}}
{{% /row %}}

<br></br>

{{% row %}}
{{% fragment class="col" %}}
#### Loss function
<small>$$L_{h,A}(X, Y) = E(h(X), Y) + \lambda F_{h,A}(X)$$</small>

{{% /fragment %}}
{{% fragment class="col" %}}
#### Binary and categorical

<small>$$WDP_{h, A}(X) = \sum_{a \in A} \left\|\left\| E[h(X) \mid A{=}a] - E[h(X)] \right\|\right\| \cdot w_{a}$$</small>
<small>$$WDI_{h, A}(X) = \sum_{a \in A} \eta\left(\frac{E\left[h(X) \mid A{=}a\right]}{E\left[h(X) \mid A{\ne}a\right]}\right) \cdot w_{a}$$</small>
<small>$$WEO_{h, A}(X) = \sum_{(a, y)}^{A \times Y} eo_{h, A}(X, a, y) \cdot w_{a}$$</small>

{{% /fragment %}}
{{% fragment class="col" %}}
#### Continuous
<small>$$GDP_{h, A}(X) = \int_{l}^{u}(\left\|\left\|E[h(X) \mid A{=}a] - E[h(X)]\right\|\right\| \cdot w_{a}) \cdot da$$</small>
<small>$$GDI_{h, A}(X) = \int_{l}^{u} \eta\left(\frac{E\left[h(X) \mid A{=}a\right]}{E\left[h(X) \mid A{\ne}a\right]}\right) \cdot w_{a} \cdot da$$</small>
<small>$$GEO_{h, A}(X) = \int_{l}^{u} \sum_{(a, y)}^{A \times Y} (eo_{h, A}(X, a, 0) + eo_{h, A}(X, a, 1)) \cdot w_{a} \cdot da$$</small>
{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Results on the Adult dataset {.accent}

{{% row %}}
{{% fragment class="col" %}}

#### Gender (binary)
    
{{< image height="30" src="/demographic_parity_sex.png" >}}
{{< image height="30" src="/equalized_odds_sex.png" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

#### Ethnicity (categorical)

{{< image height="30" src="/demographic_parity_ethnicity.png" >}}
{{< image height="30" src="/equalized_odds_ethnicity.png" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

#### Age (continuous)

{{< image height="30" src="/demographic_parity_age.png" >}}
{{< image height="30" src="/equalized_odds_age.png" >}}
    
{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Future directions {.highlight}

{{% row %}}
{{% fragment class="col" %}}
#### Intersectionality {.accent}

FaUCI can already be used to **consider multiple protected attributes** (subgroups) at the same time.
However, we still need to perform a wide empirical study of the method to understand its performance.
$$L_{h,\bar{A}}(X, Y) = E(h(X), Y) + \lambda_{1} F_{h,A_1}(X) + \dots + \lambda_{n} F_{h,A_n}(X)$$

{{% /fragment %}}
{{% /row %}}

{{% row %}}
{{% fragment class="col" %}}

#### Language for fairness {.accent}

We want to develop a **language** to help users to define **ad-hoc fairness constraints** in a more intuitive way.
Many potential users do not have a strong background in ML and statistics, so we aim to **make fairness techniques more accessible**.
This is something very similar to what happen with *symbolic knowledge injection* methods.

{{% /fragment %}}
{{% fragment class="col" %}}

#### AutoML for fairness {.accent}

Because the training of ML models requires many hyperparameters -- and with the addition of fairness constraints there is usually one more -- we want to use AutoML tools to study the **convergence of the best hyperparameters** and how well they perform.
In this way we can fairly compare different fairness techniques and understand which one is the best.

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-big.html" transition="zoom" %}}
## Thank you for your attention! {.highlight}
<br></br>
{{< image height="10" src="/aequitas-logo.svg" >}}