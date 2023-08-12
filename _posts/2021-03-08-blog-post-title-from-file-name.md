## Test

Due to a plugin called `jekyll-titles-from-headings` which is supported by GitHub Pages by default. The above header (in the markdown file) will be automatically used as the pages title.

If the file does not start with a header, then the post title will be derived from the filename.

This is a sample blog post. You can talk about all sorts of fun things here.

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
