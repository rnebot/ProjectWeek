Back to [Projects List](../../README.md#ProjectsList)

# DICOM WSI: conversion into DICOM WSI, analysis workflows operating on WSI, using DICOM WSI from IDC

## Key Investigators

- Maximilian Fischer (German Cancer Research Center, Germany)
- Andrey Fedorov (Brigham and Women’s Hospital, USA)
- Marco Nolden (German Cancer Research Center, Germany)
- Philipp Schader (German Cancer Research Center, Germany)
- David Clunie (PixelMed Publishing, USA)
- Daniela Schacherer (Fraunhofer MEVIS, Germany)
- André Homeyer (Fraunhofer MEVIS, Germany)
- Curtis Lisle (KnowledgeVis, USA)

**[Project channel on Discord: #dicom-wsi](https://discord.com/channels/843934857620357130/1069591021928853574)**


# Project Description

<!-- Add a short paragraph describing the project. -->
The Imaging Data Commons (IDC) portal is a cloud based repository of public cancer imaging data, and inclludes access to histopathological image data in the DICOM standard. In recent years increasingly more automated image analysis algorithms for pathology data emerged. However they are mainly developed for proprietary WSI vendor file formats and not for the standardized DICOM WSI file format as input. In this project a tumor classification algorithm shall be developed for DICOM WSI files as input file format. 
The aim of this project is to develop an end to end Google Colab notebook to define a data cohort from the IDC database. The selected cohort is retrieved in the DICOM WSI standard and an examplary deep learning based image analysis algorithm is applied on the selected DICOM studies. As a use case task we select a classification algorithm, which is a common downstream task in computational pathology. The algorithm generates for the selected DICOM WSI files a tumor heatmap and provides the analysis result as DICOM parametric map, which can be visualized together with WSI image in the interoperable web-based slide microscopy viewer and annotation tool (SLIM), which is fully integrated in the IDC database. 
A basis of this project provides the DICOM WSI support in the Kaapana platform, which also shall be improved in this project. The custom DICOM conversion pipeline for WSI files, which is integrated in the platform shall be improved and further applications with DICOM WSI data integrated in the platform. 






## Objective

<!-- Describe here WHAT you would like to achieve (what you will have as end result). -->

1. An analysis pipeline to visualize the analysis results for IDC digital pathology data 
2. Deploy a deep learning based tumor classification algorithm via Google Colab
3. Develop further pathology applications in the Kaapana platform

## Approach and Plan

<!-- Describe here HOW you would like to achieve the objectives stated above. -->

1. Define Query/Retrieve operations to define a data cohort from IDC portal
2. Test several image analysis algorithms for tumor classification
3. Store the result in a DICOM WSI file format 
4. Integrate workflow in Google Colab

## Progress and Next Steps

<!-- Update this section as you make progress, describing of what you have ACTUALLY DONE. If there are specific steps that you could not complete then you can describe them here, too. -->
1. Had a project kick-off meeting to discuss the plan.
   * Agreed for Max and Andrey will work to set up initial part of the colab notebook that searches and downloads WSI from IDC and extracts tiles, then this can be used both by Max and Curt for workflow development
   * Agreed to use Colab notebook to set up conversion pipeline using David and google converter
2. Curt Tested multiple DICOM-WSI converters using a pyramidal Aperio cancer image from NCI.  Both Google's wsi2dicom and the wsidicomizer converted the image, but   **wsidicomizer** did a better job including DICOM metadata. (See high-res example inset below)
3. A pyramidal whole slide image becomes a set of DICOM images, one file per level of the pyramid.  DICOM header information connect the files together. Not all conversions agreed on the number of pyramid levels, but wsidicomizer preserved all levels. 
5. ...

# Illustrations
A small feature preserved correctly at 40x resolution by **wsidicomizer**
![High res ROI preserved by conversion](https://user-images.githubusercontent.com/2152950/216401551-d743f74e-b2f5-415d-aadf-f0b0ad1b6643.png)



# Background and References

<!-- If you developed any software, include link to the source code repository. If possible, also add links to sample data, and to any relevant publications. -->

- worfklow used by IDC to create DICOM WSI: [https://github.com/ImagingDataCommons/idc-wsi-conversion](https://github.com/ImagingDataCommons/idc-wsi-conversion)
- Colab notebooks with examples of using DICOM WSI in analysis workflows: [https://github.com/ImagingDataCommons/IDC-Examples/tree/master/notebooks/pathomics](https://github.com/ImagingDataCommons/IDC-Examples/tree/master/notebooks/pathomics)
- DICOM WSI converter from Google: [https://github.com/GoogleCloudPlatform/wsi-to-dicom-converter](https://github.com/GoogleCloudPlatform/wsi-to-dicom-converter)
- sample image [https://cytomine.com/collection/cmu-1/cmu-1-svs](https://cytomine.com/collection/cmu-1/cmu-1-svs)
- Dropbox folder for storing related artifacts: https://www.dropbox.com/sh/2wkpn4iypxyvg7o/AACkI5F9f2yk42Jp9a2uat02a?dl=0
- Max github repo: https://github.com/maxfscher/DICOMwsiWorkflow
- Colab Notebook for the conversion process https://colab.research.google.com/drive/1sbuGggwmbE-JgkO8LS5ndXIzLpf7yhKd?usp=sharing
- Slim deployment instructions (WIP): https://docs.google.com/document/d/1r6r8w4FZnzeQO47TDn9DTj78nTjDsxuy4jSULmrCTwM/edit
- wsidicomizer repository: https://github.com/imi-bigpicture/wsidicomizer
