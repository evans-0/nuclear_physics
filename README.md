# Nuclear Physics ⚛️

Computational nuclear physics programs written in both **C** and **Fortran** to calculate nuclear properties from atomic mass data. Given the number of protons, mass number, and atomic mass of a nucleus, the programs compute the **mass excess**, **binding energy**, and **binding energy per nucleon**.

Both implementations use high-precision CODATA physical constants and produce results in **MeV**.

![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![Fortran](https://img.shields.io/badge/Fortran-734F96?style=for-the-badge&logo=fortran&logoColor=white)

---

## 📁 Structure

```
nuclear_physics/
├── mass_excess.c      # C implementation
├── mass_excess.f90    # Fortran 90 implementation
└── README.md
```

---

## ⚛️ Physics

### Input

| Symbol | Description |
|--------|-------------|
| `Z` | Number of protons |
| `A` | Mass number (protons + neutrons) |
| `m` | Atomic mass in amu |

Neutron count is derived as `N = A − Z`.

### Computed Quantities

**Mass Excess** — difference between actual atomic mass and mass number, in energy units:

```
Δ = (m − A) · u · c² / (e · 10⁶)   [MeV]
```

**Binding Energy** — energy required to completely separate all nucleons:

```
BE = (Z·mₚ + Z·mₑ + N·mₙ − m) · u · c² / e   [MeV]
```

**Binding Energy per Nucleon:**

```
BE/A = BE / (Z + N)   [MeV]
```

### Physical Constants Used

| Constant | Value |
|----------|-------|
| Atomic mass unit `u` | 1.6605390666050 × 10⁻²⁷ kg |
| Proton mass `mₚ` | 1.00727646662153 amu |
| Neutron mass `mₙ` | 1.0086649158849 amu |
| Electron mass `mₑ` | 5.4857990907016 × 10⁻⁴ amu |
| Speed of light `c` | 299,792,458 m/s |
| Elementary charge `e` | 1.602176634 × 10⁻¹⁹ C |

---

## 💻 Usage

### C

```bash
gcc mass_excess.c -o mass_excess
./mass_excess
```

### Fortran

```bash
gfortran mass_excess.f90 -o mass_excess_f
./mass_excess_f
```

---

## 🧪 Example — Carbon-12 (⁶C¹²)

**C output** (`long double` — ~18 significant digits):

```
Enter no. of protons: 6
Enter mass number: 12
Enter mass(in amu): 12

Excess mass energy -> 0.000000 MeV
Binding energy -> 92.161816 MeV
Binding energy per nucleon -> 7.680151 MeV
```

**Fortran output** (`real*16` — ~34 significant digits):

```
Enter no. of protons: 6
Enter mass number: 12
Enter mass(in amu): 12

Mass excess =    0.00000000000000000000000000000000000     MeV
Binding energy =    92.1618149954628507274327674679800925  MeV
Binding energy per nucleon =    7.68015124962190422728606395566500796  MeV
```

> The Fortran `real*16` quad precision gives **34 significant digits** compared to C's `long double`, demonstrating why Fortran remains the language of choice in high-precision scientific computing.

---

## 🔬 Precision Comparison

| Implementation | Type | Significant Digits |
|----------------|------|--------------------|
| C | `long double` | ~18–19 |
| Fortran | `real*16` | ~33–34 |

---

## ⚖️ License

This project is licensed under the [GPL-2.0 License](./LICENSE).
