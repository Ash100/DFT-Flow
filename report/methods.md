### Computational methods

Starting structures were generated from SMILES with RDKit [1] using the ETKDGv3 distance-geometry algorithm [2,3] (30 conformers, 0.3 Å RMSD pruning), relaxed with the MMFF94 force field [4], and the 5 lowest conformers were re-optimised at the GFN2-xTB level [5] with tblite through ASE [6]. The lowest-energy conformer whose covalent connectivity was preserved was taken forward.

All density functional theory (DFT) calculations were carried out with PySCF 2.14.0 [7] with GPU acceleration through GPU4PySCF [8,9] and exchange–correlation functionals from Libxc [10]. Geometries were optimised at the B3LYP-D3(BJ)/def2-SVP level (B3LYP functional [11], Grimme's D3(BJ) dispersion correction [12,13], def2-SVP basis set [14]), using the geomeTRIC optimiser with translation–rotation internal coordinates [15] and Gaussian-equivalent default convergence criteria (maximum force 4.5×10⁻⁴ Eh/bohr, RMS force 3.0×10⁻⁴ Eh/bohr). SCF energies were converged to 10⁻⁹ Eh on a level-3 integration grid. The resolution-of-identity (density-fitting) approximation was used for Coulomb and exchange integrals with the def2-universal-JKFIT auxiliary basis [16].

Harmonic vibrational frequencies were obtained from analytic Hessians at the optimisation level to confirm that each structure is a minimum (no imaginary frequencies) and to compute zero-point energies, enthalpies and Gibbs free energies at 298.15 K and 1 atm within the rigid-rotor/harmonic-oscillator approximation [17] (unscaled). Infrared intensities were computed analytically from atomic polar tensors and spectra were broadened with Lorentzian functions (FWHM 20 cm⁻¹).

Electronic properties were computed by single-point calculations at the B3LYP-D3(BJ)/def2-TZVP level (B3LYP functional [11], Grimme's D3(BJ) dispersion correction [12,13], def2-TZVP basis set [14]) on the optimised geometries. Global reactivity descriptors were derived from Koopmans' approximation [18] and from vertical ΔSCF ionisation energies and electron affinities (N±1 electron systems at fixed geometry): electronegativity χ = (I+A)/2, chemical hardness η = (I−A)/2 [19], softness S = 1/(2η), electrophilicity ω = χ²/(2η) [20], and electron-accepting/donating powers ω⁺ and ω⁻ [21].

Atomic charges were obtained by Hirshfeld partitioning [22] using spherically averaged free-atom densities computed with the same basis set, together with Mulliken charges [23]. Condensed Fukui functions [24,25] f⁺, f⁻ and f⁰ were evaluated by finite differences of Hirshfeld charges of the N, N+1 and N−1 electron systems, and the dual descriptor Δf = f⁺ − f⁻ [26] was used to identify electrophilic and nucleophilic sites.

The molecular electrostatic potential (MEP) was evaluated exactly on the 0.001 au electron-density isosurface [27,28], extracted from a 64³ density grid by the marching-cubes algorithm [29,30], and quantified with the Murray–Politzer surface descriptors (V_S,min, V_S,max, Π, σ²_tot, ν) [31]. Frontier orbitals were visualised at ±0.03 au.

Vertical excitation energies and oscillator strengths of the lowest 10 excited states were calculated by linear-response TD-DFT [32,33] at the CAM-B3LYP [34]/def2-TZVP level on the optimised geometries; UV-Vis spectra were simulated by Gaussian broadening (σ = 0.4 eV).

The protocol was validated against experimental equilibrium structures and dipole moments of water, formaldehyde and ammonia [35]; 9 of 10 benchmark quantities were reproduced within tolerance (±0.025 Å, ±2.5°, ±0.25 D).

The complete workflow was executed with the BinFoLab DFT-Flow notebook (v1.0); 3D structures were inspected with 3Dmol.js [36].

### References

1. RDKit: Open-source cheminformatics software. https://www.rdkit.org
2. Riniker, S.; Landrum, G. A. Better informed distance geometry: using what we know to improve conformation generation. J. Chem. Inf. Model. 2015, 55, 2562–2574.
3. Wang, S.; Witek, J.; Landrum, G. A.; Riniker, S. Improving conformer generation for small rings and macrocycles based on distance geometry and experimental torsional-angle preferences. J. Chem. Inf. Model. 2020, 60, 2044–2058.
4. Halgren, T. A. Merck molecular force field. I. Basis, form, scope, parameterization, and performance of MMFF94. J. Comput. Chem. 1996, 17, 490–519.
5. Bannwarth, C.; Ehlert, S.; Grimme, S. GFN2-xTB—An accurate and broadly parametrized self-consistent tight-binding quantum chemical method with multipole electrostatics and density-dependent dispersion contributions. J. Chem. Theory Comput. 2019, 15, 1652–1671.
6. Larsen, A. H. et al. The atomic simulation environment—a Python library for working with atoms. J. Phys.: Condens. Matter 2017, 29, 273002.
7. Sun, Q. et al. Recent developments in the PySCF program package. J. Chem. Phys. 2020, 153, 024109.
8. Li, R.; Sun, Q.; Zhang, X.; Chan, G. K.-L. Introducing GPU acceleration into the Python-based simulations of chemistry framework. J. Phys. Chem. A 2025, 129, 1459–1468.
9. Wu, X.; Sun, Q.; Pu, Z.; Zheng, T.; Ma, W.; Yan, W.; Yu, X.; Wu, Z.; Huo, M.; Li, X.; Ren, W.; Gong, S.; Zhang, Y.; Gao, W. Enhancing GPU-acceleration in the Python-based simulations of chemistry framework. arXiv:2404.09452, 2024.
10. Lehtola, S.; Steigemann, C.; Oliveira, M. J. T.; Marques, M. A. L. Recent developments in libxc—A comprehensive library of functionals for density functional theory. SoftwareX 2018, 7, 1–5.
11. Becke, A. D. Density-functional thermochemistry. III. The role of exact exchange. J. Chem. Phys. 1993, 98, 5648–5652; Lee, C.; Yang, W.; Parr, R. G. Phys. Rev. B 1988, 37, 785–789; Stephens, P. J.; Devlin, F. J.; Chabalowski, C. F.; Frisch, M. J. J. Phys. Chem. 1994, 98, 11623–11627.
12. Grimme, S.; Antony, J.; Ehrlich, S.; Krieg, H. A consistent and accurate ab initio parametrization of density functional dispersion correction (DFT-D) for the 94 elements H–Pu. J. Chem. Phys. 2010, 132, 154104.
13. Grimme, S.; Ehrlich, S.; Goerigk, L. Effect of the damping function in dispersion corrected density functional theory. J. Comput. Chem. 2011, 32, 1456–1465.
14. Weigend, F.; Ahlrichs, R. Balanced basis sets of split valence, triple zeta valence and quadruple zeta valence quality for H to Rn: design and assessment of accuracy. Phys. Chem. Chem. Phys. 2005, 7, 3297–3305.
15. Wang, L.-P.; Song, C. Geometry optimization made simple with translation and rotation coordinates. J. Chem. Phys. 2016, 144, 214108.
16. Weigend, F. Accurate Coulomb-fitting basis sets for H to Rn. Phys. Chem. Chem. Phys. 2006, 8, 1057–1065.
17. McQuarrie, D. A. Statistical Mechanics; University Science Books: Sausalito, CA, 2000.
18. Koopmans, T. Über die Zuordnung von Wellenfunktionen und Eigenwerten zu den einzelnen Elektronen eines Atoms. Physica 1934, 1, 104–113.
19. Parr, R. G.; Pearson, R. G. Absolute hardness: companion parameter to absolute electronegativity. J. Am. Chem. Soc. 1983, 105, 7512–7516.
20. Parr, R. G.; Szentpály, L. v.; Liu, S. Electrophilicity index. J. Am. Chem. Soc. 1999, 121, 1922–1924.
21. Gázquez, J. L.; Cedillo, A.; Vela, A. Electrodonating and electroaccepting powers. J. Phys. Chem. A 2007, 111, 1966–1970.
22. Hirshfeld, F. L. Bonded-atom fragments for describing molecular charge densities. Theor. Chim. Acta 1977, 44, 129–138.
23. Mulliken, R. S. Electronic population analysis on LCAO–MO molecular wave functions. I. J. Chem. Phys. 1955, 23, 1833–1840.
24. Parr, R. G.; Yang, W. Density functional approach to the frontier-electron theory of chemical reactivity. J. Am. Chem. Soc. 1984, 106, 4049–4050.
25. Yang, W.; Mortier, W. J. The use of global and local molecular parameters for the analysis of the gas-phase basicity of amines. J. Am. Chem. Soc. 1986, 108, 5708–5711.
26. Morell, C.; Grand, A.; Toro-Labbé, A. New dual descriptor for chemical reactivity. J. Phys. Chem. A 2005, 109, 205–212.
27. Bader, R. F. W.; Carroll, M. T.; Cheeseman, J. R.; Chang, C. Properties of atoms in molecules: atomic volumes. J. Am. Chem. Soc. 1987, 109, 7968–7979.
28. Murray, J. S.; Politzer, P. The electrostatic potential: an overview. WIREs Comput. Mol. Sci. 2011, 1, 153–163.
29. Lewiner, T.; Lopes, H.; Vieira, A. W.; Tavares, G. Efficient implementation of Marching Cubes' cases with topological guarantees. J. Graphics Tools 2003, 8, 1–15.
30. van der Walt, S. et al. scikit-image: image processing in Python. PeerJ 2014, 2, e453.
31. Murray, J. S.; Lane, P.; Brinck, T.; Paulsen, K.; Grice, M. E.; Politzer, P. Relationships of critical constants and boiling points to computed molecular surface properties. J. Phys. Chem. 1993, 97, 9369–9373.
32. Runge, E.; Gross, E. K. U. Density-functional theory for time-dependent systems. Phys. Rev. Lett. 1984, 52, 997–1000.
33. Casida, M. E. Time-dependent density functional response theory for molecules. In Recent Advances in Density Functional Methods, Part I; Chong, D. P., Ed.; World Scientific: Singapore, 1995; pp 155–192.
34. Yanai, T.; Tew, D. P.; Handy, N. C. A new hybrid exchange–correlation functional using the Coulomb-attenuating method (CAM-B3LYP). Chem. Phys. Lett. 2004, 393, 51–57.
35. Johnson, R. D., III, Ed. NIST Computational Chemistry Comparison and Benchmark Database, NIST Standard Reference Database 101. https://cccbdb.nist.gov/
36. Rego, N.; Koes, D. 3Dmol.js: molecular visualization with WebGL. Bioinformatics 2015, 31, 1322–1324.