
## Illustration of the difference between causal and noncausal filtering

![hippo](./filter_animation.gif)


## Time lag and waveform distortion of causal filters

A linear filter can be expressed as the convolution of an input signal
$`x[t]`$ with the filter’s impulse response  $`h[\tau]`$:

$$
y[t] = \sum_{\tau=-\infty}^{\infty} x[t-\tau]h[\tau].
$$

It is causal if $`h[\tau<0]=0`$.

A filter’s frequency response is given by the Fourier transformation of
$`h[\tau]`$:

$$
H(\omega)= \mathcal{F}\{h[\tau]\} = A(\omega)e^{j\theta(\omega)}.
$$

where $`A(\omega)`$ is the magnitude gain or attenuation, and $`\theta(\omega)`$ the phase shift.

For an ideal filter, $`A(\omega)`$ equals 1 in the passband and 0 elsewhere.
Realizable filters deviate from this, causing **magnitude distortion**.
Achieving sharper magnitude transitions requires higher-order IIR
filters or wider FIR filters.

**Causal filters necessarily introduce phase shift (time lag)**. To see
this, note that since $`h[\tau]`$ is real, the frequency response has the
symmetry *A*(−*ω*) = *A*(*ω*), *θ*(−*ω*) = −*θ*(*ω*). If phase shift
*θ*(*ω*) = 0 for all *ω*, then *H*(*ω*) is real and *h*\[*τ*\] must be
even (*h*\[−*τ*\] = *h*\[*τ*\]), which contradicts the causality
condition *h*\[*τ*\] = 0 for *τ* \< 0, unless *h*\[*τ*\] = 0 for all
*τ*. Thus, any nontrivial causal filter must impose frequency-dependent
phase shifts, i.e. time lags. In contrast, **noncausal zero-phase**
filters can be implemented by applying a causal filter forward and
backward, as with the Butterworth filter (ncF10) used in our and in
prior studies .

**Relative phase shifts between frequency components cause waveform
distortion**. If the phase response is linear,
*θ*(*ω*) = *ω**τ*<sub>*g*</sub>, then all components experience the same
group delay *τ*<sub>*g*</sub> and the waveform shape is preserved. FIR
filters achieve this when *h*\[*τ*\] is symmetric or antisymmetric
around its midpoint (e.g. FIR1/2 in this study). The drawback is that
sharp frequency selectivity requires a long impulse response, producing
large delays equal to half the filter width. IIR filter, by contrast,
cannot achieve exact linear phase without becoming unstable.
Consequently, filter design involves balancing time lag, waveform
fidelity, and computational cost. In practice, Butterworth filters often
provide a favorable trade-off, as illustrated by the best-performing
causal filter (*c**F*1) in our study.

**Illustrations:** Three examples were presented to demonstrate the
phase shift and waveform distortion in causal filters: 1) a
moving-average filter (Avg10, Fig.
<a href="#fig:filter_avg10" data-reference-type="ref"
data-reference="fig:filter_avg10">[fig:filter_avg10]</a>), 2) a
linear-phase FIR filter with Hamming window (Fig.
<a href="#fig:filter_hamming" data-reference-type="ref"
data-reference="fig:filter_hamming">[fig:filter_hamming]</a>), and 3) a
Butterworth IIR filter (Fig.
<a href="#fig:filter_butt" data-reference-type="ref"
data-reference="fig:filter_butt">[fig:filter_butt]</a>). As shown, time
lag is intrinsic to causal filtering due to the inevitable phase shifts.
Waveform distortion arise either from nonlinear phase response (e.g.
Butterworth), or from imperfect magnitude response even in linear-phase
filters (e.g. Avg10 and Hamming).
