[![Build Status](https://travis-ci.org/JuliaGNSS/PhasedArrayTracking.jl.svg?branch=master)](https://travis-ci.org/JuliaGNSS/PhasedArrayTracking.jl)
[![Coverage Status](https://coveralls.io/repos/github/JuliaGNSS/PhasedArrayTracking.jl/badge.svg?branch=master)](https://coveralls.io/github/JuliaGNSS/PhasedArrayTracking.jl?branch=master)

# PhasedArrayTracking
This extends [Tracking.jl](https://github.com/JuliaGNSS/Tracking.jl) to support phased antenna arrays.

## Getting started

Install:
```julia
] add https://github.com/JuliaGNSS/PhasedArrayTracking.jl.git
```

## Usage

```julia
using PhasedArrayTracking
import PhasedArrayTracking: Hz
gpsl1 = PhasedArrayTracking.GPSL1()
carrier_doppler = 100Hz
code_phase = 120
inits = TrackingInitials(gpsl1, carrier_doppler, code_phase)
sample_freq = 2.5e6Hz
interm_freq = 0Hz
prn = 1
track = init_tracking(Val(4), gpsl1, inits, sample_freq, interm_freq, prn) # 4 antenna channels
beamform(x) = x[:,1] # first Antenna
track, track_results = track(signal, beamform) # signal must be of shape #samples x #antennas
```
