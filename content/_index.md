 
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
**2nd Aequitas Workshop on Fairness and Bias in AI**

🎤 *Matteo Magnini*, **Giovanni Ciatto**, **Roberta Calegari**, **Andrea Omicini**

📧 [matteo.magnini@unibo.it](mailto:gianluca.aguzzi@unibo.it)

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Context {.highlight}
### What do we mean by fairness? {.accent}

Fairness has different meanings to us depending on our *personal background*.

{{% row %}}
{{% fragment class="col" %}}

{{< image height="20" src="/woman-judge-light-skin-tone-svgrepo-com.svg" >}} {{< image height="20" src="/balance-law-svgrepo-com_v2.svg" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{< image height="20" src="/businessman-svgrepo-com.svg" >}} {{< image height="20" src="/money-cash-svgrepo-com.svg" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{< image height="20" src="/technologist-medium-skin-tone-svgrepo-com.svg" >}} {{< image height="20" src="/free-technology-icon.svg" >}}

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

It is the **simplest case**, where the protected attribute can take only two values.
There are only two groups to be considered, the classic example is the gender.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Categorical

The protected attribute can take more than two values.
Here things start to get tricky, as we might **consider all the groups for fairness**.
Examples are ethnicity, education, and occupation.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Continuous

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

{{% /fragment %}}
{{% fragment class="col" %}}

#### Which metric?
 
- Demographic/statistical parity: how much model's predictions are **independent** of the protected attribute. 
- Disparate impact: how much the model **disproportionately** affects a group.
- Equalized odds: how much the model **equally predicts** a given output for all the groups.

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Fairness under Constraints Injection {.accent}

We design FaUCI in order to be *agnostic* to the fairness metric used and to the protected attribute type:
- we considered **demographic parity**, **disparate impact**, and **equalized odds** (any other metric can be used)
- we generalized the metric to work with **binary**, **categorical**, and **continuous** protected attributes
- we also considered ad-hoc weights for the groups to cover *corner cases* (e.g., strong imbalance)

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Results on the Adult dataset {.accent}

{{% row %}}
{{% fragment class="col" %}}

#### Gender
    
{{< image height="30" src="/demographic_parity_sex.png" >}}
{{< image height="30" src="/equalized_odds_sex.png" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

#### Ethnicity

{{< image height="30" src="/demographic_parity_ethnicity.png" >}}
{{< image height="30" src="/equalized_odds_ethnicity.png" >}}

{{% /fragment %}}
{{% fragment class="col" %}}

#### Age

{{< image height="30" src="/demographic_parity_age.png" >}}
{{< image height="30" src="/equalized_odds_age.png" >}}
    
{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Future directions {.highlight}

{{% row %}}
{{% fragment class="col" %}}
#### Intersectionality

FaUCI can already be used to **consider multiple protected attributes** (subgroups) at the same time.
However, we still need to perform a wide empirical study of the method to understand its performance in these cases.

{{% /fragment %}}
{{% fragment class="col" %}}

#### Language for fairness

We want to develop a **language** to help users to define **ad-hoc fairness constraints** in a more intuitive way.
Many potential users do not have a strong background in ML and statistics, so we aim to **make fairness techniques more accessible**.

{{% /fragment %}}
{{% fragment class="col" %}}

#### AutoML for fairness

Because the training of ML models requires many hyperparameters -- and with the addition of fairness constraints there is usually one more -- we want to use AutoML tools to study the **convergence of the best hyperparameters** and how well they perform.

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Thank you for your attention! {.highlight}