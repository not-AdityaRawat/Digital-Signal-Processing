# Digital Signal Processing - Unit 1 Comprehensive Notes

## Table of Contents
1. Introduction to Signals, Systems and Signal Processing
2. Classification of Signals
3. Elements of Digital Signal Processing System
4. Concept of Frequency in Continuous and Discrete Time Signals
5. Periodic Sampling and Nyquist Theorem
6. Frequency Domain Representation of Sampling
7. Reconstruction of Band-Limited Signals
8. Review of Fourier and Laplace Transforms
9. Z-Transform and Inverse Z-Transform
10. Linear Convolution and Properties
11. Linear Constant Coefficient Difference Equations
12. Discrete-Time Fourier Transform (DTFT)
13. Properties of DTFT
14. Correlation of Signals
15. Important Fourier Transform Theorems

---

## 1. Introduction to Signals, Systems and Signal Processing

### Signal
- **Definition**: A signal is a function of one or more independent variables that carries information
- **Mathematical representation**: x(t) for continuous-time, x[n] for discrete-time
- **Examples**: Speech, music, images, temperature variations, stock prices

### System
- **Definition**: A system is a physical device or algorithm that performs operations on input signals to produce output signals
- **Mathematical representation**: y(t) = T{x(t)} where T represents the transformation

### Signal Processing
- **Definition**: The analysis, modification, and synthesis of signals to extract information or enhance signal quality
- **Types**:
  - Analog Signal Processing: Continuous-time signals and systems
  - Digital Signal Processing: Discrete-time signals and systems

---

## 2. Classification of Signals

### 2.1 Continuous-Time vs Discrete-Time Signals

**Continuous-Time Signals**:
- Defined for all values of time t
- Notation: x(t)
- Examples: Analog audio signals, temperature variations

**Discrete-Time Signals**:
- Defined only at discrete instants of time
- Notation: x[n] where n is an integer
- Obtained by sampling continuous-time signals

### 2.2 Analog vs Digital Signals

**Analog Signals**:
- Continuous in time and amplitude
- Can take any value within a continuous range

**Digital Signals**:
- Discrete in time and quantized in amplitude
- Can take only finite number of distinct values

### 2.3 Deterministic vs Non-deterministic Signals

**Deterministic Signals**:
- Can be described by explicit mathematical expressions
- Future values can be predicted from past values
- Examples: sin(ωt), e^(-αt)

**Non-deterministic (Random) Signals**:
- Cannot be described by explicit mathematical functions
- Characterized by statistical properties
- Examples: Noise, speech signals

### 2.4 Even vs Odd Signals

**Even Signals**: x(t) = x(-t)
- Symmetric about the y-axis
- Examples: cos(ωt), t²

**Odd Signals**: x(t) = -x(-t)
- Anti-symmetric about the origin
- Examples: sin(ωt), t

### 2.5 Periodic vs Aperiodic Signals

**Periodic Signals**: x(t) = x(t + T₀) for all t
- T₀ is the fundamental period
- Examples: sin(ωt), cos(ωt)

**Aperiodic Signals**:
- Do not repeat themselves
- Examples: Step function, impulse function

### 2.6 Energy vs Power Signals

**Energy Signals**:
- Have finite energy: E = ∫|x(t)|²dt < ∞
- Average power = 0
- Examples: Exponentially decaying signals

**Power Signals**:
- Have finite average power: P = lim(T→∞) (1/T)∫|x(t)|²dt < ∞
- Examples: Periodic signals

---

## 3. Elements of Digital Signal Processing System

### Basic DSP System Components:

1. **Analog Input Signal**: Continuous-time signal from real world
2. **Anti-aliasing Filter**: Low-pass filter to remove frequencies above Nyquist frequency
3. **Analog-to-Digital Converter (ADC)**:
   - Sampling: Converts continuous-time to discrete-time
   - Quantization: Converts continuous amplitude to discrete amplitude
4. **Digital Signal Processor**: Performs mathematical operations on digital data
5. **Digital-to-Analog Converter (DAC)**: Converts discrete-time signal back to continuous-time
6. **Reconstruction Filter**: Smooths the output to remove unwanted high-frequency components

### Advantages of DSP over Analog Processing:
- **Flexibility**: Easy to modify algorithms
- **Accuracy**: No component tolerances
- **Reproducibility**: Identical performance every time
- **Storage**: Digital signals can be stored without degradation
- **Cost**: Lower cost for complex operations

---

## 4. Concept of Frequency in Continuous and Discrete Time Signals

### Continuous-Time Frequency
- **Angular frequency**: ω (radians/second)
- **Frequency**: f = ω/(2π) (Hz)
- **Relationship**: ω = 2πf

### Discrete-Time Frequency
- **Normalized frequency**: Ω = ωT where T is sampling period
- **Digital frequency**: ω̂ = 2πf/fs where fs is sampling frequency
- **Range**: -π ≤ Ω ≤ π (principal range)

### Frequency Mapping:
- Continuous frequency ω maps to discrete frequency Ω = ωT
- Highest representable frequency in discrete domain is π (Nyquist frequency)

---

## 5. Periodic Sampling and Nyquist Theorem

### Sampling Process
**Mathematical representation**:
xs(t) = x(t) · p(t)

where p(t) = Σ δ(t - nT) is the sampling function

### Nyquist Sampling Theorem
**Statement**: A band-limited signal with maximum frequency fm can be perfectly reconstructed from its samples if the sampling frequency fs ≥ 2fm

**Mathematical condition**: fs ≥ 2fm

**Key terms**:
- **Nyquist rate**: 2fm (minimum sampling rate)
- **Nyquist frequency**: fm (maximum frequency in signal)
- **Aliasing**: Distortion caused when fs < 2fm

### Aliasing Effect
- Occurs when sampling rate is insufficient
- High-frequency components appear as low-frequency components
- Cannot be removed after sampling
- Prevention: Use anti-aliasing filter before sampling

---

## 6. Frequency Domain Representation of Sampling

### Spectral Analysis of Sampling
**Fourier transform of sampled signal**:
Xs(ω) = (1/T) Σ X(ω - kωs)

where:
- X(ω) is the Fourier transform of original signal
- ωs = 2π/T is the sampling frequency
- T is the sampling period

### Spectral Replication
- Sampling causes spectrum to repeat every ωs
- No overlap if ωs ≥ 2ωm (no aliasing)
- Overlap occurs if ωs < 2ωm (aliasing)

---

## 7. Reconstruction of Band-Limited Signals

### Ideal Reconstruction
**Mathematical formula**:
x(t) = Σ x[n] sinc((t - nT)/T)

where sinc(x) = sin(πx)/(πx)

### Practical Reconstruction
1. **Zero-order hold**: Staircase approximation
2. **Linear interpolation**: Connect samples with straight lines  
3. **Digital-to-analog conversion**: Followed by low-pass filtering

### Reconstruction Filter
- **Purpose**: Remove high-frequency components introduced by DAC
- **Type**: Low-pass filter with cutoff at fs/2
- **Requirement**: Sharp transition band for ideal reconstruction

---

## 8. Review of Fourier and Laplace Transforms

### Fourier Transform
**Forward transform**:
X(ω) = ∫ x(t)e^(-jωt) dt

**Inverse transform**:
x(t) = (1/2π) ∫ X(ω)e^(jωt) dω

### Laplace Transform
**Forward transform**:
X(s) = ∫ x(t)e^(-st) dt

**Inverse transform**:
x(t) = (1/2πj) ∫ X(s)e^(st) ds

### Key Properties:
- **Linearity**: T{ax₁(t) + bx₂(t)} = aX₁(ω) + bX₂(ω)
- **Time shifting**: x(t-t₀) ↔ X(ω)e^(-jωt₀)
- **Frequency shifting**: x(t)e^(jω₀t) ↔ X(ω-ω₀)
- **Convolution**: x(t)*h(t) ↔ X(ω)H(ω)

---

## 9. Z-Transform and Inverse Z-Transform

### Z-Transform Definition
**Forward Z-transform**:
X(z) = Σ x[n]z^(-n)

**Region of Convergence (ROC)**:
- Values of z for which X(z) converges
- Critical for determining system properties

### Inverse Z-Transform Methods
1. **Long Division Method**: Expand X(z) as power series
2. **Partial Fraction Expansion**: Decompose rational functions
3. **Contour Integration**: Use residue theorem
4. **Table lookup**: Use standard Z-transform pairs

### Common Z-Transform Pairs:
- δ[n] ↔ 1
- u[n] ↔ 1/(1-z⁻¹), |z| > 1
- aⁿu[n] ↔ 1/(1-az⁻¹), |z| > |a|
- naⁿu[n] ↔ az⁻¹/(1-az⁻¹)², |z| > |a|

### Properties of Z-Transform:
- **Linearity**: Z{ax₁[n] + bx₂[n]} = aX₁(z) + bX₂(z)
- **Time shifting**: Z{x[n-n₀]} = z^(-n₀)X(z)
- **Multiplication by n**: Z{nx[n]} = -z(dX(z)/dz)
- **Convolution**: Z{x[n]*h[n]} = X(z)H(z)

---

## 10. Linear Convolution and Properties

### Definition
**Continuous-time**:
y(t) = x(t) * h(t) = ∫ x(τ)h(t-τ) dτ

**Discrete-time**:
y[n] = x[n] * h[n] = Σ x[k]h[n-k]

### Properties of Convolution:
1. **Commutative**: x*h = h*x
2. **Associative**: x*(h*g) = (x*h)*g
3. **Distributive**: x*(h+g) = x*h + x*g
4. **Identity**: x*δ = x
5. **Shift property**: If y = x*h, then y[n-n₀] = x[n-n₀]*h[n] = x[n]*h[n-n₀]

### Graphical Convolution Steps:
1. Reflect h[k] to get h[-k]
2. Shift to get h[n-k]
3. Multiply x[k] and h[n-k]
4. Sum over all k

---

## 11. Linear Constant Coefficient Difference Equations

### General Form
**N-th order difference equation**:
Σ(k=0 to N) aₖy[n-k] = Σ(k=0 to M) bₖx[n-k]

### Solution Methods:
1. **Classical method**: Homogeneous + particular solution
2. **Z-transform method**: Transform equation, solve algebraically
3. **Recursive computation**: Direct computation from equation

### System Function
**H(z) = Y(z)/X(z) = (Σbₖz⁻ᵏ)/(Σaₖz⁻ᵏ)**

### System Properties from H(z):
- **Stability**: All poles inside unit circle
- **Causality**: ROC extends outward from outermost pole
- **FIR vs IIR**: FIR has finite impulse response, IIR has infinite

---

## 12. Discrete-Time Fourier Transform (DTFT)

### Definition
**Forward DTFT**:
X(e^(jω)) = Σ x[n]e^(-jωn)

**Inverse DTFT**:
x[n] = (1/2π) ∫ X(e^(jω))e^(jωn) dω

### Existence Condition
**Absolute summability**: Σ|x[n]| < ∞

### Relationship to Z-Transform
DTFT is Z-transform evaluated on unit circle: X(e^(jω)) = X(z)|z=e^(jω)

### Periodicity
DTFT is periodic with period 2π: X(e^(j(ω+2π))) = X(e^(jω))

---

## 13. Properties of DTFT

### Key Properties:
1. **Linearity**: ax₁[n] + bx₂[n] ↔ aX₁(e^(jω)) + bX₂(e^(jω))
2. **Time shifting**: x[n-n₀] ↔ e^(-jωn₀)X(e^(jω))
3. **Frequency shifting**: e^(jω₀n)x[n] ↔ X(e^(j(ω-ω₀)))
4. **Time reversal**: x[-n] ↔ X(e^(-jω))
5. **Conjugation**: x*[n] ↔ X*(e^(-jω))
6. **Convolution**: x[n]*h[n] ↔ X(e^(jω))H(e^(jω))
7. **Multiplication**: x[n]h[n] ↔ (1/2π)X(e^(jω))*H(e^(jω))
8. **Parseval's theorem**: Σ|x[n]|² = (1/2π)∫|X(e^(jω))|²dω

### Symmetry Properties:
- **Real signals**: X(e^(jω)) = X*(e^(-jω))
- **Even signals**: X(e^(jω)) is real and even
- **Odd signals**: X(e^(jω)) is purely imaginary and odd

---

## 14. Correlation of Signals

### Auto-correlation
**Definition**: Measure of similarity between a signal and its delayed version

**Energy signals**:
Rₓₓ(m) = Σ x[n]x*[n-m]

**Properties**:
- Maximum at m = 0: Rₓₓ(0) = Σ|x[n]|²
- Conjugate symmetry: Rₓₓ(m) = Rₓₓ*(-m)
- |Rₓₓ(m)| ≤ Rₓₓ(0)

### Cross-correlation
**Definition**: Measure of similarity between two different signals

**Formula**:
Rₓᵧ(m) = Σ x[n]y*[n-m]

**Applications**:
- Pattern matching
- Time delay estimation
- System identification

### Relationship to Convolution:
Rₓᵧ(m) = x[m] * y*[-m]

---

## 15. Important Fourier Transform Theorems

### Convolution Theorem
**Time domain convolution = Frequency domain multiplication**
x(t) * h(t) ↔ X(ω)H(ω)

### Multiplication Theorem  
**Time domain multiplication = Frequency domain convolution**
x(t)h(t) ↔ (1/2π)X(ω) * H(ω)

### Modulation Theorem
**Amplitude modulation**:
x(t)cos(ω₀t) ↔ (1/2)[X(ω-ω₀) + X(ω+ω₀)]

### Differentiation Theorem
**Time differentiation**:
dx(t)/dt ↔ jωX(ω)

**Frequency differentiation**:
tx(t) ↔ j(dX(ω)/dω)

### Integration Theorem
∫x(τ)dτ ↔ X(ω)/(jω) + πX(0)δ(ω)

---

## Key Formulas Summary

| Transform | Forward | Inverse |
|-----------|---------|---------|
| Fourier | X(ω) = ∫x(t)e^(-jωt)dt | x(t) = (1/2π)∫X(ω)e^(jωt)dω |
| Laplace | X(s) = ∫x(t)e^(-st)dt | x(t) = (1/2πj)∫X(s)e^(st)ds |
| Z-Transform | X(z) = Σx[n]z^(-n) | x[n] = (1/2πj)∮X(z)z^(n-1)dz |
| DTFT | X(e^(jω)) = Σx[n]e^(-jωn) | x[n] = (1/2π)∫X(e^(jω))e^(jωn)dω |

---

## Important Notes for Exams:
1. **Nyquist theorem**: fs ≥ 2fm
2. **Aliasing prevention**: Use anti-aliasing filter
3. **DTFT periodicity**: Period = 2π
4. **Convolution in frequency domain**: Becomes multiplication
5. **Stability condition**: All poles inside unit circle
6. **Causality condition**: ROC extends outward from outermost pole
7. **Energy vs Power signals**: Energy finite vs Power finite
8. **Even/Odd decomposition**: Any signal = even part + odd part

---

*End of Unit 1 Notes*