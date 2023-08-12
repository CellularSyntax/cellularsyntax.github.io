## Modeling the Human Sinoatrial Node

### Introduction

The heart's rhythm, that steadfast beat echoing life's very essence, begins in a specialized region known as the sinoatrial node (SAN). Understanding the SAN isn't just a matter of anatomy; it's about unraveling the electrical dance that initiates each heartbeat.

In 2017, a groundbreaking study by Alan Fabbri and colleagues [<a href="#ref1">1</a>] brought us closer to this understanding by constructing a comprehensive mathematical model of the human SAN pacemaker cell. Published in <i>The Journal of Physiology</i>, this work doesn't merely echo the rhythm of life; it deciphers its code.

Basing their model on electrophysiological data from isolated human SAN pacemaker cells and building on the Severi-DiFrancesco model of rabbit SAN cells [<a href="#ref2">2</a>], Fabbri et al. crafted a mathematical portrait that closely resembles the action potentials and calcium transient found in real human cells.

But why does this matter? It's more than a scientific curiosity. The model provides insights into the "funny current" (<i>I<sub>f</sub></i>) that modulates the heart's pacing rate. It explains how certain mutations affect heart rate, a finding that resonates with clinical observations. And perhaps most excitingly, it offers a valuable tool for designing new experiments and developing drugs that can tune the heart's rhythm.

Today, I invite you to delve into the heart of this paper with me. Let's explore the intricacies of the human SAN pacemaker cell, understand its rhythm, and appreciate the beauty of mathematical modeling in the realm of biology.

#### Model Foundation and Constraints
<p>The starting point of the work by Fabbri et al. [<a href="#ref1">1</a>] was the rabbit SAN cell model from Severi et al. [<a href="#ref2">2</a>], with enhancements derived from electrophysiological data of human cells and automatic optimization for unknown parameters. The model was influenced by various human cell data, constrained by AP parameters, voltage clamp data, effects of <i>I<sub>f</sub></i> blockers, and Ca<sup>2+</sup> transient data.  <strong><a href="#fig1">Figure 1</a></strong> shows a schematic diagram of the human SAN AP model, with compartmentalization essential for calcium handling and details on the ionic currents, pumps, and exchangers inherited from the parent model or developed independently.</p>

#### Cell Capacitance and Dimensions
<p>Cell dimensions and membrane capacitance were assumed in line with experimental data, adopting dimensions of intracellular compartments from the parent model.</p>

#### Membrane Currents
<p>Fabbri et al. [<a href="#ref1">1</a>] specified sarcolemmal currents flowing through ionic channels, pumps, and exchangers shown in <strong><a href="#fig1">Figure 1</a></strong>, except for <i>I<sub>K,ACh</sub></i>. Adjustments were made for various currents such as the funny current (<i>I<sub>f</sub></i>), rapid delayed rectifier K<sup>+</sup> current (<i>I<sub>Kr</sub></i>), slow delayed rectifier K<sup>+</sup> current (<i>I<sub>Ks</sub></i>), ultrarapid delayed rectifier K<sup>+</sup> current (<i>I<sub>Kur</sub></i>), and others. These modifications included changes in conductance, implementation of kinetic schemes, and adjustments based on experimental findings or automatic optimization.</p>

<img id="fig1" src="https://raw.githubusercontent.com/CellularSyntax/cellularsyntax.github.io/main/san_model_schematic.jpg" style="display:block;margin-left:auto;margin-right:auto"/>
<div class="figcap"><strong>Figure 1</strong> The cell is segmented into three areas: the subsarcolemma, cytosol, and sarcoplasmic reticulum (SR), with the SR further split into junctional and network sections. The handling of Calcium ions (Ca<sup>2+</sup>) is facilitated by two diffusion processes (<i>J<sub>diff</sub></i>, from subsarcolemmal to cytosol, and <i>J<sub>tr</sub></i>, from network SR to junctional SR), the uptake of Ca<sup>2+</sup> into the network SR by the SERCA pump (<i>J<sub>up</sub></i>), and the release of Ca<sup>2+</sup> from the junctional SR into the subsarcolemmal space through RyRs. There are 11 various ionic channels, pumps, and exchangers through which Sodium, Calcium, and Potassium ions move across the sarcolemmal membrane. Reproduced from Fabbri et al. [<a href="#ref1">1</a>, p.2367]
</div>

#### Calcium Handling
<p>The mathematical formulation of Ca<sup>2+</sup> handling was maintained from the parent model, but parameters were updated through automatic optimization, including aspects such as SR Ca<sup>2+</sup> uptake (<i>J<sub>up</sub></i>), SR Ca<sup>2+</sup> release (<i>J<sub>rel</sub></i>), and Ca<sup>2+</sup> diffusion and buffers.</p>

#### Ion Concentrations
<p>The model by Fabbri et al. included a detailed description of Ca<sup>2+</sup> dynamics for four compartments and fixed intracellular Na<sup>+</sup> concentration, following the whole cell configuration used in certain experiments.</p>

<p>Overall, the model by Fabbri et al. integrates detailed revisions to accurately represent human SAN cells, reflecting experimental data, and making specific modifications to currents, capacitance, Ca<sup>2+</sup> handling, and ion concentrations.</p>

#### Autonomic Modulation of the Sinoatrial Node

<p>The sinoatrial (SA) node, situated in the right atrium of the heart, is the primary pacemaker responsible for initiating the heart's rhythmic contractions. Autonomic modulation of the SA node is a critical aspect of cardiac function, allowing the heart rate to be precisely regulated in response to various physiological demands. The autonomic nervous system (ANS) influences the SA node through both its sympathetic and parasympathetic branches. Sympathetic stimulation increases the heart rate by enhancing the pacemaker currents within the SA node, preparing the body for stress or physical activity. In contrast, parasympathetic stimulation, mediated mainly through acetylcholine, reduces the heart rate by inhibiting these currents, promoting a state of rest and recovery. The balance between these two branches ensures that the heart rate is finely tuned to meet the body's needs, whether it is responding to exercise, stress, or relaxation. The modulation of the SA node by the ANS is a complex interaction involving neurotransmitters, receptors, ionic channels, and cellular signaling pathways. It is a fundamental aspect of cardiovascular regulation, with implications for overall heart health and disease management.
</p>

<p>The effects of 10 nM ACh on <em>I<sub>f</sub></em> activation (–7.5 mV shift in voltage dependence of activation), <em>I<sub>CaL</sub></em> (3.1% reduction of maximal conductance) and SR Ca<sup>2+</sup> uptake (7% decrease of maximum activity) were all adopted from the parent model [<a href="#ref2">2</a>]. The administration of ACh also activates <em>I<sub>K,ACh</sub></em>, which is zero in the default model. The <em>I<sub>K,ACh</sub></em> formulation was derived from the parent model. The maximal conductance <em>g<sub>K,ACh</sub></em> was set to 3.45 nS (reduced by 77.5%) to achieve an overall reduction of the spontaneous rate by 20.8% upon administration of 10 nM ACh, as observed by Bucchi et al.  [<a href="#ref3">3</a>] in rabbit SAN cells. The targets of isoprenaline (Iso) are <em>I<sub>f</sub></em>, <em>I<sub>CaL</sub></em>, <em>I<sub>NaK</sub></em>, maximal Ca<sup>2+</sup> uptake and <em>I<sub>Ks</sub></em>. Changes in currents were adopted from the parent model, except for the modulation of <em>I<sub>CaL</sub></em>, where the effect of Iso induced a slightly smaller decrease of the slope factor <em>k<sub>dL</sub></em> (−27% with respect to control conditions, instead of the −31% assumed by the parent model). The <em>I<sub>CaL</sub></em> current was modulated to fit the experimental data reported by Bucchi et al. [<a href="#ref3">3</a>] on rabbit SAN cells (26.3±5.4%; mean±SEM, n=7) for the same Iso concentration [<a href="#ref1">1</a>].</p>


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
  </li>
  <li><strong>OpenCOR Software</strong>: This tool allows us to export the CellML model as Python, bridging the gap between biological understanding and computational implementation. Download OpenCOR at <a href="https://opencor.ws/" target="_blank" rel="noopener noreferrer">this link</a>.</li>
  <li><strong>CellML Model of Fabbri et al.</strong>: The specific blueprint we'll be exploring, this model is key to our journey. You can find it readily available at <a href="https://models.cellml.org/e/568/HumanSAN_Fabbri_Fantini_Wilders_Severi_2017.cellml/view" target="_blank" rel="noopener noreferrer">this location</a>.</li>
</ol>
<b>Note: </b>You can install the Python packages using the following command:<br/>

```python
pip install numpy scipy matplotlib
```

<p>Once you've gathered these components, you'll be well-prepared to follow along as we explore the computational intricacies of the human sinoatrial node model.</p>

### Python Code Generation from CellML File
<p>Generating Python code from a CellML file is a straightforward process, and OpenCOR makes it a breeze. With just one command, you can transform the Fabbri model into executable Python code. Here's how:</p>
<ol>
  <li>Open your command line or shell interface.</li>
  <li>Navigate to the directory where OpenCOR and the CellML file are located.</li>
  <li><b>Open your shell and execute the following command to generate a Python file from the specified CellML model:</b>
  </li>
</ol>

```python
$ ./OpenCOR -c CellMLTools::export HumanSAN_Fabbri_Fantini_Wilders_Severi_2017.cellml python.xml
```

<p>If you'd like to dive deeper into the code generation process and explore additional options, more detailed information is available on the <a href="https://tutorial-on-cellml-opencor-and-pmr.readthedocs.io/en/latest/code_generation.html" target="_blank" rel="noopener noreferrer">OpenCOR website</a>.</p>
<p>With the code successfully generated, you're ready to move on to the next steps, including model simulation and analysis. Let's get coding!</p>

### Understanding the Structure of the Generated Python Code
 <p>This section offers an in-depth examination of the Python code generated to simulate the Sinoatrial Node (SAN). The code is structured into various functions, each tailored to handle distinct aspects of the SAN model. Below, each function is presented with a description of its purpose.</p>

#### Size Definitions and Imports

This part of the code defines the sizes of various arrays that will be used throughout the code. It also imports all the functions from the math and NumPy modules.

```python
from math import *
from numpy import *
# Variable array sizes
sizeAlgebraic = 101
sizeStates = 33
sizeConstants = 116
```

#### Create Legends and Labels

The <code>createLegends</code> function initializes and sets legends or descriptions for states, algebraic variables, variable of integration (voi) or time, and constants. This can be useful for annotating plots or for providing context to the values within the code.


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
    return legend_states, legend_algebraic, legend_voi, legend_constants
```

#### Initialize Constants and States

The <code>initConsts</code> function initializes the constants and states arrays. The constants are values that do not change during the simulation, whereas the states represent the initial state of the system and can be altered as the system evolves.

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
    return states, constants
```

#### Compute Rates

The <code>computeRates</code> function computes the rate of change of the states based on the current values of states, constants, and variable of integration (voi). This function is essential for the numerical integration step where the system evolves over time.

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
    return rates
```

#### Compute Algebraic Variables

The <code>computeAlgebraic</code> function computes algebraic variables, which are derived from the state variables but are not part of the differential equations themselves. These can represent various quantities of interest in the model.


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

#### Piecewise Function

The <code>custom_piecewise</code> function computes the result of a piecewise-defined function. It takes as input a list of conditions and values and returns the value corresponding to the first true condition.

```python
def custom_piecewise(cases):
    """Compute result of a piecewise function"""
    return select(cases[0::2],cases[1::2])
```
#### Solve the Model

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
    return voi, states, algebraic
```

#### Plot the Results

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

### Necessary Code Modifications for Successful Execution

<p>Unfortunately, the generated code does not work out of the box, requiring some critical adjustments. This situation often occurs when automatically produced code is utilized, and it highlights the necessity of human intervention in the coding process. In brief, the following actions will be undertaken to modify the existing code to make it functional and more user-friendly:</p>
<ol>
  <li><strong>Refactoring for Readability</strong>: To enhance understanding and maintenance, the code will undergo refactoring. This process involves restructuring the existing code without changing its external behavior. It aims to improve the nonfunctional attributes of the software, making the code more readable.</li>
  <li><strong>Integration with SciPy's <code>solve_ivp</code></strong>: The existing solver will be replaced with <code>solve_ivp</code> from the SciPy library. This modification will enhance the code's efficiency, leveraging a well-optimized solver. It necessitates adapting the function signatures and updating the way the model's differential equations are defined.</li>
  <li><strong>Plotting Code Modification</strong>: To generate a better-readable figure of the states, the existing plotting code will be modified. This may involve changes in labeling, scales, and visualization styles to convey the information more effectively.</li>
  <li><strong>Object Orientation: </strong>Shifting the code structure to an object-oriented paradigm to enhance the usability and manageability of the model.</li>
</ol>
<p>These modifications will be vital to transform the raw generated code into a functional, efficient, and user-friendly script. The following sections will delve into each of these modifications, providing specific examples and guidance on implementing these changes. By following these steps, users will be able to leverage the provided code to suit their specific needs and preferences.</p>

#### 1. Definition of a Class for Sinoatrial Node Object
<p>This section of the code defines the <code>SinoAtrialNode</code> class, allowing for the creation of a Sinoatrial Node object, which represents a central component of the heart's electrical system. This class structure enables encapsulation and modularity within the code.</p>

<p>
In the Sinoatrial Node (SAN) model, ACh and Nor represent the concentrations of acetylcholine and norepinephrine, respectively, two neurotransmitters that play crucial roles in the regulation of heart rate. Acetylcholine (ACh) is usually involved in slowing down the heart rate by reducing the pacemaker current, while norepinephrine (Nor) tends to increase the heart rate by enhancing the pacemaker current. These neurotransmitters interact with specific receptors in the cardiac cells, modulating the ionic currents and thus the overall behavior of the SAN. In the context of the model, the constants c[9] and c[10] are assigned to ACh and Nor respectively, allowing their concentrations to be manipulated and thus to simulate various physiological conditions, such as stress or relaxation, that would alter the concentrations of these neurotransmitters.
</p>

```python
class SinoAtrialNode:
    def __init__(self, ACh=0, Nor=0):
        self.NUM_ALGEBRAIC = 101
        self.NUM_STATES = 33
        self.NUM_CONSTANTS = 116
        self.c = np.zeros(self.NUM_CONSTANTS)
        self.y = np.zeros(self.NUM_STATES)
        self.update(ACh, Nor)
```

#### 2. Refactoring for Better Readability
<p>The variables <code>STATES</code>, <code>ALGEBRAIC</code>, <code>CONSTANTS</code> are refactored to <code>y</code>, <code>a</code>, <code>c</code>, respectively, to improve readability and succinctness within the code. This change simplifies variable names without losing the underlying meaning.</p>

```python
self.c = np.zeros(self.NUM_CONSTANTS)
self.y = np.zeros(self.NUM_STATES)
```

#### 3. Introduction of Update Function
<p>An update function has been introduced that recalculates constants when ACh and Nor are adjusted. This function is called within the constructor, ensuring that the constants are properly initialized based on the given inputs.</p>

```python
def update(self, ACh, Nor):
    self.y[0] = -47.787168
    self.y[1] = 6.226104e-5
    self.y[2] = 5
    self.y[3] = 0.009508
    self.y[4] = 0.447724
    self.y[5] = 0.003058
    ...
```

#### 4. Constructor for Initialization
<p>The constructor method initializes all variables, including arrays for states and constants. This method sets up the initial state of the Sinoatrial Node object and ensures that it is ready for further operations.</p>

```python
def __init__(self, ACh=0, Nor=0):
    self.NUM_ALGEBRAIC = 101
    self.NUM_STATES = 33
    self.NUM_CONSTANTS = 116
    self.c = np.zeros(self.NUM_CONSTANTS)
    self.y = np.zeros(self.NUM_STATES)
    self.update(ACh, Nor)
```

#### 5. Step Function for Calculating Rates
<p>The step function calculates the rates for each step as the model advances in time. This function represents the dynamics of the system and updates the states based on the provided inputs and current state.</p>

```python
def step(self, t, y):
    a = np.zeros(self.NUM_ALGEBRAIC)
    dydt = np.zeros(self.NUM_STATES)
    self.y = y
    a[6] = self.c[69] * self.c[78] * (1.0 - (self.y[22] + self.y[18])) - self.c[75] * self.y[18]
    dydt[18] = a[6]
    a[1] = self.c[47] / (self.c[47] + self.y[1])
    a[7] = (0.001 * a[1]) / self.c[46]
    dydt[8] = (a[1] - self.y[8]) / a[7]
    ...
    return dydt
```

#### 6. Conversion of Piecewise Terms to Use NumPy
<p>The original code contained custom piecewise functions generated by the OpenOCR code generator. In this modification, those custom piecewise functions were replaced with NumPy's built-in <code>np.piecewise</code> function. This change leverages the efficiency and readability of NumPy's functions and ensures compatibility with other NumPy-based calculations within the code.</p>

```python
# Example usage of np.piecewise in the code
result = np.piecewise(x, [condition1, condition2], [value_if_condition1, value_if_condition2])
```

### Executing the Simulation with solve_ivp
<p>The simulation of the Sinoatrial Node model is executed using SciPy's <code>solve_ivp</code> function, a general-purpose solver for initial value problems with a flexible interface for defining complex systems of ordinary differential equations (ODEs). </p>

```python
import SinoAtrialNode
import numpy as np
from scipy.integrate import solve_ivp

tmax = 5  # simulation duration
san = SinoAtrialNode.SinoAtrialNode()  # generate the sinoatrial node object 
sol = solve_ivp(san.step, [0, tmax], list(san.y), method='BDF', rtol=1e-6,
                     t_eval=np.arange(0, tmax, 1e-4), vectorized=False)  # solve system
```

<p>This call to <code>solve_ivp</code> integrates the model over the specified time interval, utilizing the BDF method and the provided initial conditions, tolerances, and evaluation points to generate the simulation results.</p>
  
  
  <p>Here's a breakdown of the parameters used in the function:</p>
<ol>
  <li><code>san.step</code>: This is the step function defined in the SinoAtrialNode class, responsible for calculating the rates at which the model advances in time.</li>
  <li><code>[0, tmax]</code>: Specifies the time span of integration, from 0 to <code>tmax</code> (5 in this example), indicating the start and end times of the simulation.</li>
  <li><code>list(san.y)</code>: The initial conditions, defined as the initial state variables <code>y</code> from the Sinoatrial Node object.</li>
  <li><code>method='BDF'</code>: Specifies the solver method to be used. The 'BDF' (Backward Differentiation Formula) method is an implicit multi-step method suitable for stiff problems.</li>
  <li><code>rtol=1e-6</code>: The relative tolerance parameter, determining the accuracy of the solution.</li>
  <li><code>t_eval=np.arange(0, tmax, 1e-4)</code>: Defines the time points at which the solution is stored. It allows control over the discrete points in time for which the solver should return the system state.</li>
  <li><code>vectorized=False</code>: Indicates whether the function is implemented in a vectorized fashion. Setting this to False means that the function expects the input to be a single point in time.</li>
</ol>

<h2>Plotting the Results</h2>
<p>The following code is used to visualize the simulation results. It includes the definition of the legend labels for the different states and plots all 33 states, each in a separate subplot.</p>

```python
import matplotlib.pyplot as plt

legend_states = [
    "V_ode in Membrane (mV)",
    "Ca_sub in Ca_dynamics (mM)",
    "Nai_ in Nai_concentration (mM)",
    ...
]

plt.figure(figsize=(20, 50))
for i in range(1, 33):
    plt.subplot(17,2,i)
    plt.plot(sol.t, sol.y[i-1])
    plt.ylabel(legend_states[i-1], fontsize=10)
    plt.xlabel("Time (s)")

plt.show()
```

<p>The code produces a figure with 33 subplots, representing different states of the model (<strong><a href="#fig2">Figure 2</a></strong>). </p>

<img id="fig2" src="https://raw.githubusercontent.com/CellularSyntax/cellularsyntax.github.io/main/san_model_plot.png">
<div class="figcap"><strong>Figure 2</strong> Plot of the 33 states from the simulation. Membrane potential in millivolts (mV), concentrations in millimolar (mM), and various gates and components represented in dimensionless units (D.L.). Each subplot visualizes the evolution of a specific state over time. </div>

### References
<ol style="margin-left:20px">
<li><a href="https://doi.org/10.1113/JP273259" id="ref1">Fabbri, Alan, et al. "Computational analysis of the human sinus node action potential: model development and effects of mutations." The Journal of physiology 595.7 (2017): 2365-2396.</a></li>
<li><a href="https://doi.org/10.1113/jphysiol.2012.229435" id="ref2">Severi, Stefano, et al. "An updated computational model of rabbit sinoatrial action potential to investigate the mechanisms of heart rate modulation." The Journal of physiology 590.18 (2012): 4483-4499.</a></li>
  <li><a href="https://doi.org/10.1016/j.yjmcc.2007.04.017" id="ref3">Bucchi, Annalisa, et al. "Modulation of rate by autonomic agonists in SAN cells involves changes in diastolic depolarization and the pacemaker current." Journal of molecular and cellular cardiology 43.1 (2007): 39-48.</a></li>
</ol>
