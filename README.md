# dataset_unscrewing

## Introduction

This repo contains the data set, which has been used for the CCN-based detection of rounded screw drives.

## Dataset Structure

Each of the different datasets contains two subfolders, one containing training data and the other containing test data.
The train and test data is split by lables into `loesbar` (releasable) and `nicht_loesbar` (non_releasable) in each folder.
Each json file contains the data of one unscrewing process and contains different key values that provide information about the unscrewing process.

| ![dataset overview](canvas.jpg "The dataset overview") |
| :----------------------------------------------------: |
|                  The dataset overview                  |

## Key parameter

The tourque can be optained with following python code:

```python
path = 'your-path-to-the-dataset'
with open(path) as f:
   df = json.loads(f.read())
torque = np.array(df['tightening steps'][0]['graph']['torque values'][0:self.sequence_length])
```

The corresponding angle values have equidistant steps of 5.320°.

The file also contains other important keyvalues:

- `df['prg name']`: screw type
- `df['tightening steps']['torque']`: max tourque
- `df['tightening steps']['speed']`: max speed

| Dataset | Description               | Trial Number | Train/Test                                      |
| :-----: | ------------------------- | :----------: | ----------------------------------------------- |
|    1    | Benchmark                 |    1 & 2     | 80%/20%                                         |
|    2    | Screw Size Independency   |      3       | 80%/20% (M4,M5/M6,M8)                           |
|    3    | Screw Head Independency   |      4       | 80%/20% (Torx, E. Hexagon/ Philips, I. Hexagon) |
|    4    | Sparse Dataset1           |      5       | 20%/80%                                         |
|    5    | Sparse Dataset2           |      6       | 160/80 datasets                                 |
|    6    | Sparse Dataset3/Half Data |      7       | 80%/20%                                         |

## Used Hardware

Bosch Rexroth Nexo NXP for manual unscrewing operations
MINIMAT ®-EC-SERVO and deprag AST40 for the robot-based unscrewing operations

## Reference

```bibtex
@article{ALASSADI202219,
title = {Machine learning based screw drive state detection for unfastening screw connections},
journal = {Journal of Manufacturing Systems},
volume = {65},
pages = {19-32},
year = {2022},
issn = {0278-6125},
doi = {https://doi.org/10.1016/j.jmsy.2022.07.013},
url = {https://www.sciencedirect.com/science/article/pii/S0278612522001248},
author = {Anwar {Al Assadi} and David Holtz and Frank Nägele and Christof Nitsche and Werner Kraus and Marco F. Huber},
keywords = {Screws, Machine learning, Neural networks, Unfastening, Disassembly, Battery systems}
}
```

## License

This work is licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).

```yaml
SPDX-License-Identifier: CC-BY-4.0
```

## Acknowledgement

Sponsored by the Ministry of the Environment Baden-Württemberg, in the context of the Strategic Dialogue Automotive Industry, and supervised by the Project Management Agency Karlsruhe (PTKA). Funding number: L7520101

https://www.ipa.fraunhofer.de/de/referenzprojekte/DeMoBat.html
