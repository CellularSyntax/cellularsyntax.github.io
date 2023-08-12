## Modeling the Human Sinoatrial Node

### Introduction

The heart's rhythm, that steadfast beat echoing life's very essence, begins in a specialized region known as the sinoatrial node (SAN). Understanding the SAN isn't just a matter of anatomy; it's about unraveling the electrical dance that initiates each heartbeat.

In 2017, a groundbreaking study by Alan Fabbri and colleagues [1] brought us closer to this understanding by constructing a comprehensive mathematical model of the human SAN pacemaker cell. Published in The Journal of Physiology, this work doesn't merely echo the rhythm of life; it deciphers its code.

Basing their model on electrophysiological data from isolated human SAN pacemaker cells and building on the Severi-DiFrancesco model of rabbit SAN cells [2], Fabbri et al. crafted a mathematical portrait that closely resembles the action potentials and calcium transient found in real human cells.

But why does this matter? It's more than a scientific curiosity. The model provides insights into the "funny current" (If) that modulates the heart's pacing rate. It explains how certain mutations affect heart rate, a finding that resonates with clinical observations. And perhaps most excitingly, it offers a valuable tool for designing new experiments and developing drugs that can tune the heart's rhythm.

Today, I invite you to delve into the heart of this paper with me. Let's explore the intricacies of the human SAN pacemaker cell, understand its rhythm, and appreciate the beauty of mathematical modeling in the realm of biology.

### Prerequisites for Implementing the Human SAN Pacemaker Cell Model

<p>Before we dive into the heart of the modeling, there are some essential tools and resources you'll need to have ready:</p>
<ol>
  <li><strong>Python</strong>: The beating core of our code, Python is the programming language we'll use to bring this model to life. If you don't already have it installed, you can download it from the <a href="https://www.python.org/downloads/" target="_blank" rel="noopener noreferrer">official Python website</a>.<br/></li>
  <li><strong>Python Packages</strong>: These libraries act as the supporting vessels for our code:
    <ul>
      <li><strong>numpy</strong>: For numerical computations.</li>
      <li><strong>scipy</strong>: To leverage scientific and technical computing.</li>
      <li><strong>matplotlib</strong>: To visualize the results and plot beautiful graphs.</li>
    </ul>
    <br/>
    <b>You can install these packages using the following command:</b><br/>
    
```python
pip install numpy scipy matplotlib
```

  </li>
  <li><strong>OpenCOR Software</strong>: This tool allows us to export the CellML model as Python, bridging the gap between biological understanding and computational implementation. Download OpenCOR at <a href="https://opencor.ws/" target="_blank" rel="noopener noreferrer">this link</a>.</li>
  <li><strong>CellML Model of Fabbri et al.</strong>: The specific blueprint we'll be exploring, this model is key to our journey. You can find it readily available at <a href="https://models.cellml.org/e/568/HumanSAN_Fabbri_Fantini_Wilders_Severi_2017.cellml/view" target="_blank" rel="noopener noreferrer">this location</a>.</li>
</ol>
<p>Once you've gathered these components, you'll be well-prepared to follow along as we explore the computational intricacies of the human sinoatrial node model.</p>

### Python Code Generation from CellML File
<p>Generating Python code from a CellML file is a straightforward process, and OpenCOR makes it a breeze. With just one command, you can transform the Fabbri model into executable Python code. Here's how:</p>
<ol>
  <li>Open your command line or shell interface.</li>
  <li>Navigate to the directory where OpenCOR and the CellML file are located.</li>
  <li><b>Open your shell and execute the following command to generate a Python file from the specified CellML model:</b>

```python
$ ./OpenCOR -c CellMLTools::export myfile.cellml myformat.xml
```

  </li>
</ol>
<p>If you'd like to dive deeper into the code generation process and explore additional options, more detailed information is available on the <a href="https://tutorial-on-cellml-opencor-and-pmr.readthedocs.io/en/latest/code_generation.html" target="_blank" rel="noopener noreferrer">OpenCOR website</a>.</p>
<p>With the code successfully generated, you're ready to move on to the next steps, including model simulation and analysis. Let's get coding!</p>

### Understanding the Structure of the Generated Python Code
 <p>This section provides an overview of the generated Python code used for mathematical modeling in a particular domain. The code is divided into several functions, each with a specific role, to create, initialize, compute, and plot various mathematical and scientific parameters. Below, each function is presented with a description of its purpose.</p>

#### Size Definitions and Imports

This part of the code defines the sizes of various arrays that will be used throughout the code. It also imports all the functions from the math and NumPy modules.

```python
# Size of variable arrays:
sizeAlgebraic = 101
sizeStates = 33
sizeConstants = 116
from math import *
from numpy import *
```

#### <code>`createLegends`</code> Function

The createLegends function initializes and sets legends or descriptions for states, algebraic variables, variable of integration (voi), and constants. This can be useful for annotating plots or for providing context to the values within the code.


```python
def createLegends():
    legend_states = [""] * sizeStates
    legend_rates = [""] * sizeStates
    legend_algebraic = [""] * sizeAlgebraic
    legend_voi = ""
    legend_constants = [""] * sizeConstants
    legend_voi = "time in component environment (second)"
    legend_constants[0] = "R in component Membrane (joule_per_kilomole_kelvin)"
    legend_constants[1] = "T in component Membrane (kelvin)"
    legend_constants[2] = "F in component Membrane (coulomb_per_mole)"
    legend_constants[3] = "C in component Membrane (microF)"
    legend_constants[91] = "RTONF in component Membrane (millivolt)"
    legend_algebraic[59] = "i_f in component i_f (nanoA)"
    ...
    return (legend_states, legend_algebraic, legend_voi, legend_constants)
```

#### Function: <code>`initConsts`</code> 

The initConsts function initializes the constants and states arrays. The constants are values that do not change during the simulation, whereas the states represent the initial state of the system and can be altered as the system evolves.

```python
def initConsts():
    constants = [0.0] * sizeConstants; states = [0.0] * sizeStates;
    constants[0] = 8314.472
    constants[1] = 310
    constants[2] = 96485.3415
    constants[3] = 5.7e-5
    constants[4] = 0
    states[0] = -47.787168
    constants[5] = 0.5
    constants[6] = 0.5
    constants[7] = -35
    ...
    return (states, constants)
```

#### Function: <code>`computeRates`</code>

The computeRates function computes the rate of change of the states based on the current values of states, constants, and variable of integration (voi). This function is essential for the numerical integration step where the system evolves over time.

```python
def computeRates(voi, states, constants):
    rates = [0.0] * sizeStates; algebraic = [0.0] * sizeAlgebraic
    algebraic[6] = constants[69]*constants[78]*(1.00000-(states[22]+states[18]))-constants[75]*states[18]
    rates[18] = algebraic[6]
    algebraic[1] = constants[47]/(constants[47]+states[1])
    algebraic[7] = (0.00100000*algebraic[1])/constants[46]
    rates[8] = (algebraic[1]-states[8])/algebraic[7]
    algebraic[2] = constants[51]-(constants[51]-constants[52])/(1.00000+power(constants[53]/states[15], constants[54]))
    algebraic[8] = constants[55]/algebraic[2]
    algebraic[17] = constants[56]*algebraic[2]
    rates[11] = (constants[57]*states[14]-algebraic[17]*states[1]*states[11])-(algebraic[8]*(power(states[1], 2.00000))*states[11]-constants[58]*states[12])
    rates[12] = (algebraic[8]*(power(states[1], 2.00000))*states[11]-constants[58]*states[12])-(algebraic[17]*states[1]*states[12]-constants[57]*states[13])
    ...
    return(rates)
```

#### Function: <code>`computeAlgebraic`</code>

The computeAlgebraic function computes algebraic variables, which are derived from the state variables but are not part of the differential equations themselves. These can represent various quantities of interest in the model.


```python
def computeAlgebraic(constants, states, voi):
    algebraic = array([[0.0] * len(voi)] * sizeAlgebraic)
    states = array(states)
    voi = array(voi)
    algebraic[6] = constants[69]*constants[78]*(1.00000-(states[22]+states[18]))-constants[75]*states[18]
    algebraic[1] = constants[47]/(constants[47]+states[1])
    algebraic[7] = (0.00100000*algebraic[1])/constants[46]
    algebraic[2] = constants[51]-(constants[51]-constants[52])/(1.00000+power(constants[53]/states[15], constants[54]))
    algebraic[8] = constants[55]/algebraic[2]
    algebraic[17] = constants[56]*algebraic[2]
    algebraic[5] = custom_piecewise([greater(voi , constants[5]) & less(voi , constants[5]+constants[6]), constants[7] , True, constants[8]])
    ...
    return algebraic
```

#### Function: <code>`custom_piecewise`</code>

The custom_piecewise function computes the result of a piecewise-defined function. It takes as input a list of conditions and values and returns the value corresponding to the first true condition.

```python
def custom_piecewise(cases):
    """Compute result of a piecewise function"""
    return select(cases[0::2],cases[1::2])
```
#### Function: <code>`solve_model`</code>

The solve_model function sets up and solves the differential equations using SciPy's ODE solver. It initializes the constants and states, sets up the solver, and then integrates the system over a specified time span, returning the variable of integration, states, and algebraic variables.

```python
def solve_model():
    """Solve model with ODE solver"""
    from scipy.integrate import ode
    # Initialise constants and state variables
    (init_states, constants) = initConsts()

    # Set timespan to solve over
    voi = linspace(0, 10, 500)

    # Construct ODE object to solve
    r = ode(computeRates)
    r.set_integrator('vode', method='bdf', atol=1e-06, rtol=1e-06, max_step=1)
    r.set_initial_value(init_states, voi[0])
    r.set_f_params(constants)

    # Solve model
    states = array([[0.0] * len(voi)] * sizeStates)
    states[:,0] = init_states
    for (i,t) in enumerate(voi[1:]):
        if r.successful():
            r.integrate(t)
            states[:,i+1] = r.y
        else:
            break

    # Compute algebraic variables
    algebraic = computeAlgebraic(constants, states, voi)
    return (voi, states, algebraic)
```

#### Function: <code>`plot_model`</code> Function

The plot_model function plots the state and algebraic variables against the variable of integration. It can be used to visualize the evolution of the system over time.

```python
def plot_model(voi, states, algebraic):
    """Plot variables against variable of integration"""
    import pylab
    (legend_states, legend_algebraic, legend_voi, legend_constants) = createLegends()
    pylab.figure(1)
    pylab.plot(voi, vstack((states,algebraic)).T)
    pylab.xlabel(legend_voi)
    pylab.legend(legend_states + legend_algebraic, loc='best')
    pylab.show()
```
#### Main Execution

This part of the code is executed when the script is run directly. It calls the solve_model function to compute the results and then plots them using Matplotlib.

```python
if __name__ == "__main__":
    (voi, states, algebraic) = solve_model()
    from matplotlib import pyplot as plt
    import numpy as np
    plt.plot(states)
    plt.xlim(0,20)
    plot_model(voi, states, algebraic)
```

In summary, this code defines a system of differential equations and provides functions to initialize the system, compute the derivatives, integrate the system over time, and plot the results. The code is organized into clear functions, each with a specific role in the modeling and simulation process.

### References
<ol style="margin-left:20px">
<li><a href="https://doi.org/10.1113/JP273259">Fabbri, Alan, et al. "Computational analysis of the human sinus node action potential: model development and effects of mutations." The Journal of physiology 595.7 (2017): 2365-2396.</a></li>
<li><a href="https://doi.org/10.1113/jphysiol.2012.229435">Severi, Stefano, et al. "An updated computational model of rabbit sinoatrial action potential to investigate the mechanisms of heart rate modulation." The Journal of physiology 590.18 (2012): 4483-4499.</a></li>
</ol>
