# Torso-dynamics Estimation System (TES) Validation Study
Data processing code from validation study of the Torso-dynamics Estimation System (TES)
<br> **Corresponding paper**: (**INSERT PAPER LINK HERE**)

## Table of Contents
1. [Introduction](#introduction)
2. [Directory Structure and Required Files](#directory-structure-and-required-files)
3. [Using the Code](#using-the-code)
4. [Code File Descriptions](#code-file-descriptions)

## Introduction
The code files in this repository are used to process data was collected during a validation study of our Torso-Dynamics Estimation System (TES). The TES consisted of a Force Sensing Seat (FSS) and an inertial measurement unit (IMU) that measured the kinetics and kinematics of the subject's torso motions. The FSS estimated the 3D forces, 3D moments, and 2D COPs while the IMU estimated the 3D torso angles. To validate the TES, the FSS and IMU estimates were compared to gold standard research equipment (AMTI force plate and Qualisys motion capture system, respectively).

There were two generations of the FSS, FSS Gen 1.0 and FSS Gen 2.0. This repository contains data processing code from the validation study of each FSS generation. So, some of the code files pertain to only one of the FSS generations. Any code files with "Gen1" or "Gen2" in the name are for processing data from only that corresponding FSS generation. All other files are supporting functions that are used to process data from both FSS generations.

### Models of Equipment Used
- **Load cells (used in FSS)**
  - *FSS Gen 1.0:* DYMH-103, Calt, China (x6)
  - *FSS Gen 2.0:* CZL301C, Hualanhai, China (x6)
- **IMU:** VN-100, VectorNav, USA
- **Force plates**
  - *For FSS Gen 1.0 study:* BP600900-1K, AMTI, USA
  - *For FSS Gen 2.0 study:* OR6-7-2000, AMTI, USA
- **Motion capture cameras (x6):** Oqus 500, Qualisys, Sweden

### Note on Units
The following units were used for the validation study data:
- **3D Forces:** Newtons (N)
- **3D Moments:** Newton-meters (Nm)
- **2D Center of Pressures (COPs):** millimeters (mm)
- **3D Torso Angles:** degrees

## Directory Structure and Required Files
### Data processing code files
The MATLAB code files for processing this data can be found in [this GitHub repository](https://github.com/ssong47/TorsodynamicsEstimationSystem). The repository will have a folder named *TES Data Processing Code* that contains all the MATLAB code files needed to process this data. Note that the name of this folder corresponds to the folder of the same name in the directory structure described below.

### Directory structure
Before downloading the data files and data processing code, you need to set up your directory to match the directories used in the code. Following this directory structure will make it easier to update your directories in the code. Specifically, directories will need to be updated in the following code files:
- Gen1_aggregate_data_processing.m
- Gen2_aggregate_data_processing.m
- MAIN_data_process_Gen1study.m
- MAIN_data_process_Gen2study.m

In each of these files, there are also comments explaining the directory structure to use.

### The directory structure is as follows:

**Main folder:** *TES Design Validation Study* <br>

**Subfolders:**
- *TES Data Processing Code*
- *FSS Gen 1.0 Data*
- *FSS Gen 2.0 Data*
- *FSS Gen 1.0 Figures*
- *FSS Gen 2.0 Figures*

### The required files for each folder are as follows:
- *TES Data Processing Code:* MATLAB code files for processing the data (from this repository)
- *FSS Gen 1.0 Data:* Data from FSS Gen 1.0, IMU, AMTI force plate, and Qualisys motion capture
- *FSS Gen 2.0 Data:* Data from FSS Gen 2.0, IMU, AMTI force plate, and Qualisys motion capture
- *FSS Gen 1.0 Figures* and *FSS Gen 2.0 Figures:* Empty folders where generated figures will be saved <br>

### Data files
Due to the size of the data files, they were unable to be uploaded to this repository. Instead, they were uploaded to this IEEE DataPort **(INSERT LINK HERE)**. In this DataPort, there are two zipped folders named *FSS Gen 1.0 Data* and *FSS Gen 2.0 Data*, which correspond to the folders in the directory structure described above. You will need to unzip the folders and then put them in the directory structure.

## Using the Code
Most of the MATLAB code files in this repository are supporting functions used in the main data processing scripts. As a result, you will only need to run the main data processing scripts, which are:
- MAIN_data_process_Gen1study.m
- MAIN_data_process_Gen2study.m
- Gen1_aggregate_data_processing.m
- Gen2_aggregate_data_processing.m

First, you will need to run the MAIN script (choose Gen 1 or Gen 2 depending on which FSS validation study you want to analyze) to do the initial processing of the data. This script needs to be run for each subject and trial combination individually. Since there were some issues with the data collection, the best trials from each subject were used in the data processing. The following tables give the best trial from each subject in each FSS generation validation study. You only need to run the MAIN script for these subject/trial combinations. Note that these best trials are also listed in comments in the MAIN code files.

For the MAIN script, you can change the subject by changing the cell array *subjects* and change the trial number by changing the variable *i_trial*. In addition, the directories at the beginning of the code will need to be updated according to the directory structure mentioned in the previous section of this document. 

**For FSS Gen 1.0:**<br>
| Subject | Best Trial |
| ------ | ------ |
| S1 | 4 |
| S2 | 4 |
| S3 | 4 |
| S4 | 1 |
| S5 | 1 |
| S6 | 4 |
| S7 | 3 |
| S8 | 3 |

**For FSS Gen 2.0:**<br>
| Subject | Best Trial |
| ------ | ------ |
| S1 | 1 |
| S2 | 3 |
| S3 | 3 |
| S4 | 2 |
| S5 | 1 |
| S6 | 2 |
| S7 | 1 |
| S8 | 3 |

Once the MAIN script has been run for all subject/trial combinations, you can run the aggregate data processing script. The aggregate data processing script will use the files generated by the MAIN script, so make sure that the MAIN script has been run with all subject/trial combinations before trying to run the aggregate data processing script. In the aggregate data processing script, the subjects are defined in the cell array *subjects* while the trials for each subjects are defined in the array *trials*. You **do not** need to change these since they are already populated with the correct subject/trial combinations. However, you will still need to update the directories at the beginning of the code according to the directory structure described in the previous section.

## Code File Descriptions
All of the MATLAB code files are commented, but for quick reference, they are summarized below.
1. 

