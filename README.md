# A-COMBINATION-OF-THE-MOST-EFFECTIVE-EOR-METHODS-
Today BP investigate and impose new EOR-Specific methods, including CO2 - EOR, CCUS, LOSAL and ADVANCED GAS on wells to improve the rate of production, as well as efficiency. 

"""
# Advanced Hybrid EOR Framework for BP Assets

This repository presents technical overviews and conceptual evaluations for two 
next-generation Enhanced Oil Recovery (EOR) hybrid frameworks tailored for mature 
and deepwater reservoirs.

---

## Variant A: Smart-Water CO₂-WAG (LoSal™ + CO₂ CCUS) — *Recommended*

### Overview
Integrates BP's proprietary LoSal™ (Low Salinity Waterflooding) with Miscible CO₂ 
Water-Alternating-Gas (WAG) injection. This hybrid approach combines microscopic 
displacement efficiency with miscible macroscopic sweep, offering a dual solution 
für maximum oil recovery and carbon sequestration (CCUS).

### Synergy & Mechanisms
1. Viscosity Reduction & Swelling: Supercritical CO2 dissolves into crude oil, significantly reducing viscosity and swelling trapped droplets.
2. Wettability Alteration: LoSal™ water disrupts ionic bridges on clay surfaces, shifting matrix wettability from oil-wet to water-wet.
3. Mobility Control: Alternating gas and low-salinity water cycles suppresses early gas breakthrough while maximizing pore-scale mobilization.

---

## Variant B: Smart Conformance Flooding (LoSal™ + BrightWater®)

### Overview
Combines LoSal™ waterflooding with BrightWater® heat-activated sub-micron polymer gel 
particles to resolve volumetric sweep inefficiencies in highly heterogeneous reservoirs.

---

## Comparative Efficiency

| Feature | Variant A (LoSal™ + CO₂ WAG) | Variant B (LoSal™ + BrightWater®) |
| :--- | :--- | :--- |
| Recovery Factor Boost | +15% to 22% | +8% to 14% |
| Environmental Impact | Net-Zero aligned (CCUS) | Reduced water treatment footprint |
| Primary Target | Deepwater & Light Oil Fields | Highly Heterogeneous Mature Fields |
"""

import matplotlib.pyplot as plt
import numpy as np

def simulate_eor():
    ooip = 100.0  # Millions of Barrels (MMbbl)
    
    rf_base_waterflood = 0.35
    rf_losal_only = 0.42
    rf_hybrid_losal_co2 = 0.55

    print("=" * 45)
    print("      BP HYBRID EOR RECOVERY SIMULATION")
    print("=" * 45)
    print(f"Original Oil in Place (OOIP): {ooip} MMbbl\n")

    methods = {
        "Conventional Seawater Injection": rf_base_waterflood,
        "LoSal™ Only Injection": rf_losal_only,
        "Smart-Water CO₂-WAG Hybrid (Variant A)": rf_hybrid_losal_co2
    }

    for name, rf in methods.items():
        recovered_oil = ooip * rf
        print(f"[{name}]")
        print(f" -> Recovery Factor: {rf * 100:.1f}%")
        print(f" -> Total Produced Oil: {recovered_oil:.1f} MMbbl")
        print("-" * 45)

def plot_recovery_curves():
    time_years = np.linspace(0, 10, 100)
    
    base = 35 * (1 - np.exp(-0.4 * time_years))
    losal = 42 * (1 - np.exp(-0.45 * time_years))
    hybrid = 55 * (1 - np.exp(-0.5 * time_years))
    
    plt.figure(figsize=(9, 5))
    plt.plot(time_years, base, label="Conventional Seawater (35%)", linestyle="--", color="gray")
    plt.plot(time_years, losal, label="LoSal™ Only (42%)", linestyle="-.", color="blue")
    plt.plot(time_years, hybrid, label="Smart-Water CO₂-WAG (55%)", color="green", linewidth=2.5)
    
    plt.title("Cumulative Recovery Factor Comparison Over Time")
    plt.xlabel("Years of EOR Injection")
    plt.ylabel("Recovery Factor (%)")
    plt.grid(True, linestyle=":", alpha=0.6)
    plt.legend()
    plt.tight_layout()
    plt.savefig("recovery_profile.png")
    print("\n[+] Chart saved as 'recovery_profile.png'")

if __name__ == "__main__":
    simulate_eor()
    plot_recovery_curves()
