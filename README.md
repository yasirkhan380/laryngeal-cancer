# Laryngeal Cancer Module

## Purpose

Creation of a specific disease module for Laryngeal Cancer to be used in [Synthea<sup>TM</sup> synthetic patient generator](https://github.com/synthetichealth/synthea)

## Synthetic dataset of laryngeal cancer patients

In the 'datasets' ditionary we give you accesses to the datasets we generated and used to validate our module. If you are intressted in the results you can produce with the module feel free to analyze the datasets yourself.

Dataset C32-1 (Prevalence approach): This dataset contains XXX patients and simulates a realistic prevalence of laryngeal cancer.
Dataset C32-2 (Enriched approach): The second dataset was designed to let as many patients as possible suffer from laryngeal cancer.
Dataset C32-3 (Cohort approach):


## Installation Synthea

Testing and using of the module can be achieved after following the installation, described in [https://github.com/synthetichealth/synthea/wiki/Developer-Setup-and-Running](https://github.com/synthetichealth/synthea/wiki/Developer-Setup-and-Running). The module file needs to be pasted into the `modules` directory. Synthea by default uses all of its modules (together with intrinsic population and lifecycle data). 

## Installation the laryngeal cancer module

Modules are created using the [Module Builder](https://synthetichealth.github.io/module-builder/). Module files must be copy and pasted into the Module Builder, since it does not provide upload functionality. Files might only be stored locally in the browser cache. Hence, the git repository stores the files for the Larynx model. The respective .json-file contains the module definition. (Please notice that due to formating discrapences concering the table transition submodules that include such transitions might not be possible to open with the Module Builder)

Copy the laryngeal_cancer.json file and the dictionary laryngeal_cancer (containing the submodules) in your Synthea to:

`` src/main/resources/modules ``

Then copy all csv files from the lookup_tables dictionary in the already exsiting "lookup_tabeles" dictionary in your Synthea, therfore to:

``src/main/resources/modules/lookup_tables``

## Usage 

To generate your own patients it can be useful to first delete every module from the module dictionary you do not need to reduce unwanted 'data-trash'.

In the laryngeal cancer module you can choose between two modi:

1. This setting is the default and is used to create as many laryngeal cancer patients as possible with a realistic age distribution (which is due to the Synthea mode of operation not completly possible). Also the correct gender distribution is not taken in to account. To chnage to this mode please change in the laryngeal_cancer.json the attribute 'age_risk_distribution' to 1, which can be found in the Config-Area. For the maximal ammount of laryngeal cancer patients to be createt run this code in the terminal:

`` ./run_synthea.bat -p .... -a 40-100 ``

(`-p` giving the number of patients to be created)

2. This version creats a population with a realisitc prevalence of round about 4.7 per 100,000. Which means only a fraction of the patients will get laryngeal cancer.  To chnage to this mode please alter in the laryngeal_cancer.json the attribute 'age_risk_distribution' to 2, which can be found in the Config-Area. Run this code in the terminal:
 
 `` ./run_synthea.bat -p .... ``

To only use the larynx module, run this code in the terminal:
NOTE: ``-m`` is not recommended to be used because it can make synthea act in unexpected ways. Use at own risk. Its not necessary to use it, if you delete all module you do not need. 

`` ./run_synthea -m ... -p ...``

(with `-m` giving the name of the module without file extension, e.g., _laryngeal_cancer_, and `-p` giving the number of patients to be created; see [here](https://github.com/synthetichealth/synthea/blob/master/README.md))

## Sources

Our aim was to base every transition on either a distribution from papers and articels or creat the transition as a logical statement based on guidelines (mainly the german [S3-guideline](https://www.leitlinienprogramm-onkologie.de/leitlinien/larynxkarzinom/)). The exact source for every transiton can be found in the 'remarks' area of the pervious state.
