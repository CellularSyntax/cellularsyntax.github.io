## Modeling the Human Sinoatrial Node

### Welcome to the Beat of Life: Modeling the Human Sinoatrial Node

The heart's rhythm, that steadfast beat echoing life's very essence, begins in a specialized region known as the sinoatrial node (SAN). Understanding the SAN isn't just a matter of anatomy; it's about unraveling the electrical dance that initiates each heartbeat.

In 2017, a groundbreaking study by Alan Fabbri and colleagues [1] brought us closer to this understanding by constructing a comprehensive mathematical model of the human SAN pacemaker cell. Published in The Journal of Physiology, this work doesn't merely echo the rhythm of life; it deciphers its code.

Basing their model on electrophysiological data from isolated human SAN pacemaker cells and building on the Severi-DiFrancesco model of rabbit SAN cells [2], Fabbri et al. crafted a mathematical portrait that closely resembles the action potentials and calcium transient found in real human cells.

But why does this matter? It's more than a scientific curiosity. The model provides insights into the "funny current" (If) that modulates the heart's pacing rate. It explains how certain mutations affect heart rate, a finding that resonates with clinical observations. And perhaps most excitingly, it offers a valuable tool for designing new experiments and developing drugs that can tune the heart's rhythm.

Today, I invite you to delve into the heart of this paper with me. Let's explore the intricacies of the human SAN pacemaker cell, understand its rhythm, and appreciate the beauty of mathematical modeling in the realm of biology.

<b>References:</b> 
<ol style="margin-left:20px">
<li><a href="https://doi.org/10.1113/JP273259">Fabbri, Alan, et al. "Computational analysis of the human sinus node action potential: model development and effects of mutations." The Journal of physiology 595.7 (2017): 2365-2396.</a></li>
<li><a href="https://doi.org/10.1113/jphysiol.2012.229435">Severi, Stefano, et al. "An updated computational model of rabbit sinoatrial action potential to investigate the mechanisms of heart rate modulation." The Journal of physiology 590.18 (2012): 4483-4499.</a></li>
</ol>
---

### This is a header

#### Some Python Code

```python
import scipy.integrate 
import matplotlib.pyplot as plt
import cardiovascular.system as sys
import numpy as np
from collections import deque
from cardiovascular.heart import Atria
from cardiovascular.heart import Valves
from cardiovascular.heart import Ventricles
from cardiovascular.circulation import Veins
from cardiovascular.circulation import Arteries
from cardiovascular.nervoussystem import AfferentPathway
from cardiovascular.nervoussystem import EfferentPathway
from cardiovascular.nervoussystem import Effectors
from cardiovascular.respiration import Lung
from cardiovascular.heart import SinoAtrialNode
import cardiovascular.config as cfg
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
