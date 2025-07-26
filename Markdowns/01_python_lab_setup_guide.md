# 🐍 Python Programming Lab Setup Guide

**Title:** Python 3 Environment Setup for Electrical Engineering Lab  
**Purpose:** Complete installation guide for Python 3, VS Code, Jupyter Notebook, and Virtual Environments on Manjaro Linux and Windows 11  
**Target OS:** Manjaro Linux & Windows 11  
**Version:** V1.1  
**Written on:** July 19, 2025  
**Revision Date:** July 19, 2025  
**Author:** Kingsuk Majumdar  
**Copyright (c) 2025 Kingsuk Majumdar**

---

## 📋 Prerequisites and System Requirements


![Python](https://img.shields.io/badge/Python-3.13-blue?style=for-the-badge&logo=python)
![VS Code](https://img.shields.io/badge/VS%20Code-Latest-007ACC?style=for-the-badge&logo=visualstudiocode)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![Manjaro](https://img.shields.io/badge/Manjaro-Linux-35BF5C?style=for-the-badge&logo=manjaro)
![Windows](https://img.shields.io/badge/Windows-11-0078D4?style=for-the-badge&logo=windows)
![Virtual Environment](https://img.shields.io/badge/Virtual-Environment-green?style=for-the-badge&logo=python)


---

## 🐧 Part A: Installation on Manjaro Linux

### Step 1: Update System Packages 🔄

Open terminal and execute the following commands:

```bash
sudo pacman -Syu
```

### Step 2: Install Python 3.13 🐍

Manjaro typically comes with Python pre-installed, but to ensure we have the latest version:

```bash
# Check current Python version
python --version
python3 --version

# Install Python 3.13 if needed
sudo pacman -S python python-pip python-virtualenv

# Verify installation
python3 --version
pip --version
```

### Step 3: Install Essential Python Packages 📦

```bash
# Install commonly used packages for electrical engineering
pip install numpy matplotlib scipy pandas jupyter notebook ipykernel
pip install sympy control-systems-python
```

### Step 4: Install VS Code on Manjaro 💻

#### Method 1: Using Pacman ( NOT Recommended)
```bash
# Install VS Code from official repositories
sudo pacman -S code
```

#### Method 2: Using AUR (Alternative)
```bash
# If not available in official repos RECOMEMDED FOR M$ VS Code
yay -S visual-studio-code-bin
```

### Step 5: Install VS Code Extensions 🔌

Launch VS Code and install these essential extensions:

1. **Python Extension Pack**
   - Extension ID: `ms-python.python`
   - Extension ID: `ms-python.pylint`
   - Extension ID: `ms-python.autopep8`

2. **Jupyter Extensions**
   - Extension ID: `ms-toolsai.jupyter`
   - Extension ID: `ms-toolsai.jupyter-keymap`
   - Extension ID: `ms-toolsai.jupyter-renderers`

3. **Additional Helpful Extensions**
   - Extension ID: `ms-python.black-formatter`
   - Extension ID: `charliermarsh.ruff`

### Step 6: Configure Python Interpreter in VS Code 🔧

1. Open VS Code
2. Press `Ctrl + Shift + P` to open command palette
3. Type "Python: Select Interpreter"
4. Choose the Python 3.13 interpreter (usually `/usr/bin/python3`)

---

## 🪟 Part B: Installation on Windows 11

### Step 1: Download and Install Python 3.13 📥

1. Visit [python.org](https://python.org/downloads/)
2. Download Python 3.13 for Windows
3. **Important:** Check "Add Python to PATH" during installation
4. Choose "Customize installation" and ensure pip is selected

### Step 2: Verify Python Installation ✅

Open Command Prompt or PowerShell:

```cmd
python --version
pip --version
```

### Step 3: Install Essential Packages 📦

```cmd
pip install numpy matplotlib scipy pandas jupyter notebook ipykernel
pip install sympy control-systems-python virtualenv
```

### Step 4: Install VS Code on Windows 💻

1. Visit [code.visualstudio.com](https://code.visualstudio.com/)
2. Download VS Code for Windows
3. Run the installer with default settings

### Step 5: Install VS Code Extensions 🔌

Same extensions as listed in the Manjaro section above.

### Step 6: Configure Python Interpreter 🔧

1. Open VS Code
2. Press `Ctrl + Shift + P`
3. Type "Python: Select Interpreter"
4. Select the Python 3.13 interpreter from the list

---

## 🌐 Part C: Understanding and Working with Virtual Environments

### What is a Virtual Environment? 🤔

A virtual environment is an isolated Python environment that allows you to:

- **📦 Package Isolation:** Different projects can have different package versions
- **🔒 Dependency Management:** Avoid conflicts between project requirements  
- **🧹 Clean Development:** Keep global Python installation clean
- **🚀 Reproducibility:** Share exact environment configurations
- **🛡️ Security:** Prevent system-wide package corruption

### Significance in Electrical Engineering Projects 🔬

1. **Power System Analysis:** Different simulation tools may require specific package versions
2. **Control System Design:** MATLAB bridge packages might conflict with other tools
3. **IoT Projects:** Hardware-specific libraries need isolation
4. **Research Work:** Reproducible results for publication and collaboration

### Creating Virtual Environments

#### On Manjaro Linux 🐧

```bash
# Navigate to your project directory
cd ~/EE_Projects/Lab01

# Create virtual environment
python3 -m venv ee_lab_env

# Activate virtual environment
source ee_lab_env/bin/activate

# Your prompt should change to show (ee_lab_env)
# Install packages specific to this project
pip install numpy matplotlib jupyter

# Deactivate when done
deactivate

# To delete a virtual environment use
rm -rf ee_lab_env
# ⚠️ **Caution**: `rm -rf` is **dangerous**
trash ee_lab_env 
# trash is safer ; to install in Arch/Manjaro use #sudo pacman -S trash-cli 
```

#### On Windows 11 🪟

```cmd
# Navigate to your project directory
cd C:\EE_Projects\Lab01

# Create virtual environment
python -m venv ee_lab_env

# Activate virtual environment
ee_lab_env\Scripts\activate

# Your prompt should change to show (ee_lab_env)
# Install packages specific to this project
pip install numpy matplotlib jupyter

# Deactivate when done
deactivate
```

### Using Virtual Environments in VS Code 🔧

1. **Open VS Code in project folder**
2. **Activate virtual environment** (using commands above)
3. **Select Python interpreter:**
   - Press `Ctrl + Shift + P`
   - Type "Python: Select Interpreter"
   - Choose the interpreter from your virtual environment:
     - Linux: `./ee_lab_env/bin/python`
     - Windows: `.\ee_lab_env\Scripts\python.exe`

### Best Practices for Virtual Environments 📋

```bash
# Create requirements.txt to track dependencies
pip freeze > requirements.txt

# Install from requirements.txt in new environment
pip install -r requirements.txt

# Always activate environment before working
# Check active environment
which python  # Linux
where python   # Windows
```

---

## 📓 Part D: Setting Up Jupyter Notebook in VS Code

### Step 1: Create a New Jupyter Notebook 📝

1. Open VS Code
2. Press `Ctrl + Shift + P`
3. Type "Jupyter: Create New Jupyter Notebook"
4. Save the file with `.ipynb` extension

### Step 2: Select Python Kernel 🎯

1. Click on the kernel selector in the top-right corner of the notebook
2. Choose "Python 3.13" or the appropriate Python interpreter
3. If kernel doesn't appear, install ipykernel:

```bash
# On both systems (with virtual environment activated)
pip install ipykernel
python -m ipykernel install --user --name=ee_lab_env --display-name="EE Lab Environment"
```

### Step 3: Test Your Setup ✨

Create a new cell and run this test code:

```python
import numpy as np
import matplotlib.pyplot as plt
import sys

print(f"Python version: {sys.version}")
print(f"NumPy version: {np.__version__}")

# Simple test plot
x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x)

plt.figure(figsize=(8, 4))
plt.plot(x, y, 'b-', linewidth=2, label='sin(x)')
plt.grid(True, alpha=0.3)
plt.xlabel('x (radians)')
plt.ylabel('Amplitude')
plt.title('Test Plot - Sine Wave')
plt.legend()
plt.show()

print("✅ Setup completed successfully!")
```

---

## 👋 Part E: Hello World Programs

### 🔥 Hello World in VS Code (Python Script)

**Step 1:** Create a new file called `hello_world.py`

**Step 2:** Add the following code:

```python
"""
Title: Hello World Program for Electrical Engineering Lab
Purpose: First Python program to verify setup and demonstrate basic functionality
Compiler: Python 3.13
OS: Manjaro Linux / Windows 11
Version: V1
Written on: July 19, 2025
Revision Date: July 19, 2025
Author: Kingsuk Majumdar
Copyright (c) 2025 Kingsuk Majumdar
"""

import os
import numpy as np
import matplotlib.pyplot as plt
from datetime import datetime

def main():
    # Get the directory where the Python script is located
    script_dir = os.path.dirname(os.path.abspath(__file__))
    output_dir = os.path.join(script_dir, 'OUTPUT')
    os.makedirs(output_dir, exist_ok=True)
    
    # Hello World message
    print("🎓 Welcome to Electrical Engineering Python Lab!")
    print("=" * 50)
    print("Hello World from Dr. B. C. Roy Engineering College!")
    print("Department: Electrical Engineering")
    print("Course: Python Programming for EE Applications")
    print(f"Date: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
    print("=" * 50)
    
    # Demonstrate basic calculations relevant to EE
    voltage = 230  # RMS voltage in Volts
    current = 10   # RMS current in Amperes
    power = voltage * current
    
    print(f"📊 Basic Electrical Calculations:")
    print(f"Voltage (V): {voltage} V")
    print(f"Current (I): {current} A") 
    print(f"Power (P): {power} W")
    
    # Create a simple plot
    create_sample_plot(output_dir)
    
    print(f"\n✅ Program executed successfully!")
    print(f"📁 Output files saved in: {output_dir}")

def create_sample_plot(output_dir):
    """Create a sample AC waveform plot"""
    
    # Generate AC waveform data
    t = np.linspace(0, 2*np.pi, 1000)
    voltage_wave = 230 * np.sqrt(2) * np.sin(t)  # Peak voltage
    current_wave = 10 * np.sqrt(2) * np.sin(t - np.pi/6)  # Current with phase lag
    
    # Create the plot
    plt.figure(figsize=(12, 6))
    
    plt.subplot(1, 2, 1)
    plt.plot(t, voltage_wave, 'b-', linewidth=2, label='Voltage')
    plt.plot(t, current_wave, 'r-', linewidth=2, label='Current')
    plt.grid(True, alpha=0.3)
    plt.xlabel('Time (radians)')
    plt.ylabel('Amplitude')
    plt.title('AC Voltage and Current Waveforms')
    plt.legend()
    
    plt.subplot(1, 2, 2)
    power_wave = voltage_wave * current_wave
    plt.plot(t, power_wave, 'g-', linewidth=2, label='Instantaneous Power')
    plt.grid(True, alpha=0.3)
    plt.xlabel('Time (radians)')
    plt.ylabel('Power (W)')
    plt.title('Instantaneous Power')
    plt.legend()
    
    plt.tight_layout()
    
    # Save the plot
    plot_path = os.path.join(output_dir, 'hello_world_ac_analysis.png')
    plt.savefig(plot_path, dpi=300, bbox_inches='tight')
    plt.show()
    
    print(f"📈 Plot saved as: {plot_path}")

if __name__ == "__main__":
    main()
```

**Step 3:** Run the program by pressing `F5` or using the Run button in VS Code

---

### 📓 Hello World in Jupyter Notebook

**Step 1:** Create a new Jupyter notebook called `hello_world_lab.ipynb`

**Step 2:** Add the following cells:

#### Cell 1 (Markdown):
```markdown
# 🎓 Hello World - Electrical Engineering Lab

**Course:** Python Programming for EE Applications  
**Institution:** Dr. B. C. Roy Engineering College, Durgapur  
**Department:** Electrical Engineering  
**Author:** Kingsuk Majumdar  

---

## 📋 Lab Objectives
- Verify Python and Jupyter setup
- Demonstrate basic EE calculations
- Create visualizations for electrical parameters
- Establish project workflow
```

#### Cell 2 (Code):
```python
"""
Title: Hello World Jupyter Notebook for EE Lab
Purpose: Interactive demonstration of Python capabilities for electrical engineering
Compiler: Python 3.13 (Jupyter Kernel)
OS: Manjaro Linux / Windows 11
Version: V1
Written on: July 19, 2025
Author: Kingsuk Majumdar
Copyright (c) 2025 Kingsuk Majumdar
"""

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from datetime import datetime
import os

# Configuration for plots
plt.rcParams['figure.figsize'] = (10, 6)
plt.rcParams['font.size'] = 12

print("🔬 Electrical Engineering Python Lab - Hello World!")
print("=" * 60)
print(f"📅 Session Date: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
print("🎯 Lab Focus: Basic Python Setup and EE Applications")
print("=" * 60)
```

#### Cell 3 (Code):
```python
# 🧮 Basic Electrical Engineering Calculations

print("⚡ Three-Phase Power System Analysis")
print("-" * 40)

# System parameters
V_line = 400  # Line voltage in Volts
V_phase = V_line / np.sqrt(3)  # Phase voltage
I_line = 25   # Line current in Amperes
power_factor = 0.85  # Power factor

# Power calculations
P_total = np.sqrt(3) * V_line * I_line * power_factor  # Active power
Q_total = np.sqrt(3) * V_line * I_line * np.sin(np.arccos(power_factor))  # Reactive power
S_total = np.sqrt(P_total**2 + Q_total**2)  # Apparent power

# Create results DataFrame
results = pd.DataFrame({
    'Parameter': ['Line Voltage', 'Phase Voltage', 'Line Current', 
                  'Active Power', 'Reactive Power', 'Apparent Power', 'Power Factor'],
    'Value': [V_line, V_phase, I_line, P_total/1000, Q_total/1000, S_total/1000, power_factor],
    'Unit': ['V', 'V', 'A', 'kW', 'kVAR', 'kVA', '-']
})

print(results.to_string(index=False))
```

#### Cell 4 (Code):
```python
# 📊 Visualization: Three-Phase Voltage Waveforms

# Time vector
t = np.linspace(0, 2*np.pi, 1000)
frequency = 50  # Hz
omega = 2 * np.pi * frequency

# Three-phase voltages
V_a = V_phase * np.sqrt(2) * np.sin(omega * t)
V_b = V_phase * np.sqrt(2) * np.sin(omega * t - 2*np.pi/3)
V_c = V_phase * np.sqrt(2) * np.sin(omega * t - 4*np.pi/3)

# Create visualization
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 8))

# Three-phase waveforms
ax1.plot(t, V_a, 'r-', linewidth=2, label='Phase A')
ax1.plot(t, V_b, 'g-', linewidth=2, label='Phase B') 
ax1.plot(t, V_c, 'b-', linewidth=2, label='Phase C')
ax1.grid(True, alpha=0.3)
ax1.set_xlabel('Time (radians)')
ax1.set_ylabel('Voltage (V)')
ax1.set_title('Three-Phase Voltage Waveforms (50 Hz)')
ax1.legend()

# Phasor diagram
angles = np.array([0, -2*np.pi/3, -4*np.pi/3])
magnitudes = np.array([V_phase, V_phase, V_phase])

ax2.quiver(0, 0, magnitudes[0]*np.cos(angles[0]), magnitudes[0]*np.sin(angles[0]), 
           angles='xy', scale_units='xy', scale=1, color='red', width=0.005, label='Phase A')
ax2.quiver(0, 0, magnitudes[1]*np.cos(angles[1]), magnitudes[1]*np.sin(angles[1]), 
           angles='xy', scale_units='xy', scale=1, color='green', width=0.005, label='Phase B')
ax2.quiver(0, 0, magnitudes[2]*np.cos(angles[2]), magnitudes[2]*np.sin(angles[2]), 
           angles='xy', scale_units='xy', scale=1, color='blue', width=0.005, label='Phase C')

ax2.set_xlim(-300, 300)
ax2.set_ylim(-300, 300)
ax2.grid(True, alpha=0.3)
ax2.set_xlabel('Real Part (V)')
ax2.set_ylabel('Imaginary Part (V)')
ax2.set_title('Three-Phase Phasor Diagram')
ax2.legend()
ax2.set_aspect('equal')

plt.tight_layout()
plt.show()

print("✅ Three-phase analysis completed successfully!")
```

#### Cell 5 (Markdown):
```markdown
## 🎯 Key Learning Outcomes

1. ✅ **Environment Setup**: Python, VS Code, and Jupyter are properly configured
2. ✅ **Virtual Environment**: Project isolation implemented
3. ✅ **Basic Calculations**: Three-phase power system analysis performed
4. ✅ **Data Visualization**: Waveforms and phasor diagrams created
5. ✅ **Professional Documentation**: Proper code structure and documentation

---

## 🚀 Next Steps for Lab Work

- **Power System Analysis**: Load flow studies, fault analysis
- **Control Systems**: Transfer functions, Bode plots, stability analysis  
- **Power Electronics**: Converter circuits, PWM analysis
- **Machine Learning**: Predictive maintenance, load forecasting
- **IoT Integration**: Sensor data acquisition and processing

---

**Lab Session Complete! Ready for advanced electrical engineering applications.**
```

---

## 🛠️ Troubleshooting Common Issues

### Issue 1: Python Not Found in PATH (Windows)
**Solution:** Reinstall Python with "Add to PATH" option checked

### Issue 2: Jupyter Kernel Not Available
**Solution:** 
```bash
pip install ipykernel
python -m ipykernel install --user
```

### Issue 3: VS Code Extensions Not Working
**Solution:** 
1. Reload VS Code window (`Ctrl + Shift + P` → "Developer: Reload Window")
2. Check Python interpreter selection

### Issue 4: Permission Issues (Manjaro)
**Solution:**
```bash
# Use user installation for packages
pip install --user package_name
```

### Issue 5: Virtual Environment Not Activating
**Solution:**
```bash
# Linux: Check script permissions
chmod +x ee_lab_env/bin/activate

# Windows: Check execution policy
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

---

## 📚 Essential Packages for Electrical Engineering

```python
# Core scientific computing
import numpy as np
import matplotlib.pyplot as plt
import scipy as sp
import pandas as pd

# Electrical engineering specific
import control  # Control systems
import sympy   # Symbolic mathematics

# For lab work
import jupyter
```

---

## 🎯 Project Structure Best Practices

```
EE_Projects/
├── Lab01_HelloWorld/
│   ├── ee_lab_env/          # Virtual environment
│   ├── hello_world.py       # Python script
│   ├── hello_world_lab.ipynb  # Jupyter notebook
│   ├── requirements.txt     # Package dependencies
│   └── OUTPUT/              # Generated files
│       ├── hello_world_ac_analysis.png
│       └── session_log.txt
├── Lab02_PowerAnalysis/
├── Lab03_ControlSystems/
└── README.md
```

---

## 📞 Support and Resources

- **Python Documentation:** [docs.python.org](https://docs.python.org)
- **VS Code Python Guide:** [code.visualstudio.com/docs/python](https://code.visualstudio.com/docs/python)
- **Jupyter Documentation:** [jupyter.org/documentation](https://jupyter.org/documentation)
- **Virtual Environment Guide:** [docs.python.org/3/tutorial/venv.html](https://docs.python.org/3/tutorial/venv.html)


---

*Document prepared for Electrical Engineering Laboratory - Dr. B. C. Roy Engineering College, Durgapur*
_Prepared by 👨‍🏫  : Kingsuk Majumdar  
**Assistant Professor, Electrical Engineering**
**Revision Date:** July 19, 2025  
**Status:** ✅ Tested and Verified  
**Environment:** 🐧 Manjaro Linux & 🪟 Windows 11
