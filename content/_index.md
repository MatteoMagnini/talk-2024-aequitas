 
+++

title = "Enforcing Fairness via Constraint Injection with FaUCI"
description = "Enforcing Fairness via Constraint Injection with FaUCI"
outputs = ["Reveal"]
aliases = [
    "/guide/"
]

+++

{{% slide preload=true background-iframe="logo_unibo.svg" transition="zoom" style="background-size: 150px; background-position: top center; background-repeat: no-repeat;" %}}

# Enforcing Fairness via Constraint Injection with FaUCI
**2nd Aequitas Workshop on Fairness and Bias in AI**

🎤 *Matteo Magnini*, **Giovanni Ciatto**, **Roberta Calegari**, **Andrea Omicini**

📧 [matteo.magnini@unibo.it](mailto:gianluca.aguzzi@unibo.it)

---

{{% slide auto-animate=true %}}
## Context {.highlight}
### What do we mean by fairness? {.accent}


---

{{% slide auto-animate=true %}}
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

{{% slide auto-animate=true %}}
## Context {.highlight}
### The in-processing techniques {.accent}

---
    
{{% slide auto-animate=true %}}
## Open challenges {.highlight}
### Types of protected attributes {.accent}

---

{{% slide auto-animate=true %}}
## Open challenges {.highlight}
### Fairness metrics {.accent}

---

{{% slide auto-animate=true %}}
## FaUCI {.highlight}
### Fairness under Constraints Injection {.accent}

---

{{% slide auto-animate=true %}}
## FaUCI {.highlight}
### Results {.accent}

---

## Future directions {.highlight}


---

{{% slide auto-animate=true %}}
## Thank you for your attention! {.highlight}