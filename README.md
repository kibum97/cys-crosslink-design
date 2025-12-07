# cys-crosslink-design

Utilities to design and rank cysteine positions for crosslinking experiments. This pipeline filters candidates based on geometric compatibility and energetic stability using FoldX.

## Workflow

1. **Geometric Screen**: Uses `biopython` to identify residue pairs with compatible $C\beta-C\beta$ distances.
2. **Stability Assessment**: Uses **FoldX** (`BuildModel`) to calculate $\Delta\Delta G$ of the double mutation.
3. **Angular Ranking**: Measures $\chi_3$ torsion angles and bond lengths on the FoldX-generated mutant models.

## Dependencies

* Python 3.x
* `biopython`
* `pandas`
* `numpy`
* **FoldX 5.0** (Must be obtained separately from [FoldX](https://foldxsuite.crg.eu/))

## Usage

### Phase 1: Screen Geometry
Run the initial screen to generate the mutation list:
```bash
python scripts/geometric_screen.py --pdb your_protein.pdb
