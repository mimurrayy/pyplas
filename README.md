# pyplas - Basic library for low-temperature plasmas

The library contains a few very basic classes to store information about a low-temperature plasma and allows for the calculation of common plasma parameters.
It's mainly meant to support other libraries that do actually useful things with this basic framework, like  [**owlspec**](https://github.com/mimurrayy/owl).

Install from [pypi](https://pypi.org/project/pyplas/): `pip install pyplas`

## Example

```python
#!/bin/python3
import pyplas
from scipy import constants as const

n0 = 1e15
electrons = pyplas.electrons(n0, T=3*const.eV/const.k)
ions = pyplas.ions("Ar", n0, T=500)
neutrals = pyplas.neutrals("Ar", P=300)
plasma = pyplas.plasma(electrons, ions, neutrals, B=0.1)
print("Electron temperature (K): " + str(plasma.Te))
plasma.ion_neutral_cx = 1e-18
LD = plasma.get_Debye()
col_freq = plasma.get_ion_neutral_freq()

print("Ion gyro radius (mm): " + str(plasma.get_ion_gyro_radius()*1e3))
```    
