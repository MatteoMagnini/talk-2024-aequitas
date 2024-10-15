 
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

{{% row %}}
{{% fragment class="col" %}}
{{< image height="20" src="/woman-judge-light-skin-tone-svgrepo-com.svg" >}}
{{% /fragment %}}
{{% fragment class="col" %}}
{{< image height="20" src="/balance-law-svgrepo-com_v2.svg" >}}
{{% /fragment %}}
{{% /row %}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{% row %}}
{{% fragment class="col" %}}
{{< image height="20" src="/businessman-svgrepo-com.svg" >}}
{{% /fragment %}}
{{% fragment class="col" %}}
{{< image height="20" src="/money-cash-svgrepo-com.svg" >}}
{{% /fragment %}}
{{% /row %}}

{{% /fragment %}}
{{% fragment class="col" %}}

{{% row %}}
{{% fragment class="col" %}}
{{< image height="20" src="/technologist-medium-skin-tone-svgrepo-com.svg" >}}
{{% /fragment %}}
{{% fragment class="col" %}}
{{< image height="20" src="/free-technology-icon.svg" >}}
{{% /fragment %}}
{{% /row %}}

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
#### Metric computation

{{% /fragment %}}
{{% fragment class="col" %}}

#### Regularization

{{% /fragment %}}
{{% fragment class="col" %}}

#### Training

{{% /fragment %}}
{{% /row %}}


---
    
{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Open challenges {.highlight}
### Types of protected attributes {.accent}

{{% row %}}
{{% fragment class="col" %}}
#### Binary

{{% /fragment %}}
{{% fragment class="col" %}}

#### Categorical

{{% /fragment %}}
{{% fragment class="col" %}}

#### Continuous

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Open challenges {.highlight}
### Fairness metrics {.accent}

{{% row %}}
{{% fragment class="col" %}}
#### Group vs. Individual fairness

{{% /fragment %}}
{{% fragment class="col" %}}

#### Which metric?

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Fairness under Constraints Injection {.accent}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## FaUCI {.highlight}
### Results {.accent}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Future directions {.highlight}

{{% row %}}
{{% fragment class="col" %}}
#### Intersectionality

{{% /fragment %}}
{{% fragment class="col" %}}

#### Language for fairness

{{% /fragment %}}
{{% fragment class="col" %}}

#### AutoML for fairness

{{% /fragment %}}
{{% /row %}}

---

{{% slide auto-animate=true preload=true background-iframe="logo-right.html" transition="zoom" %}}
## Thank you for your attention! {.highlight}