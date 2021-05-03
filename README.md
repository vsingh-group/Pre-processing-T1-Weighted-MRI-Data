# Pre Processing T1-weighted MRI Data

## [Freesurfer Processing](Freesurfer%20Processing)
  The first common step shared by all of the methods was that all the T1 weighted images from ADNI-2 were segmented using FreeSurfer [Fischl et al. (2002)](https://pubmed.ncbi.nlm.nih.gov/11832223/). Developed by the Laboratory for Computational Neuroimaging at the Athinoula A. Martinos Center for Biomedical Imaging, FreeSurfer is a software package that is used for analysing and visualizing neuroimaging data.

  Freesurfer download and install steps can be foud [here](https://surfer.nmr.mgh.harvard.edu/fswiki/DownloadAndInstall)

- ### [Condor](Freesurfer%20Processing/Condor%20)
   [Condor setup](Freesurfer%20Processing/Condor%20) for Freesurfer processing

- ### [Local](/Freesurfer%20Processing/Local)
   We will generate all of the images mentioned above with the command recon-all, which only requires a T1-weighted anatomical image with good contrast between the white matter and the grey matter. Once you Download and Install Freesurfer you can run the following command. More information [here](/Freesurfer%20Processing/Local)
   
   ```recon-all -s sub-101 -i sub-mri-image.nii.gz -all```
 
   The ```-s``` option specifies the subject name, which you can set to whatever you want. The ```-i``` option points to the anatomical image that you will analyze; and the ```-all``` option will run all of the preprocessing steps on your data.


## [Freesurfer output Processing for CNNs and 3D-CNNs](Image%20Processing%20for%20CNNs) 
For CNNs the normalized and skull-stripped 3D images produced by FreeSurfer recon-all command can be used. 
- We then matched the axis and orientation of each image to that of the MNI template. 
- Then we aligned each scan to the MNI152 T1 2mm brain template using FSL affine registration. 

Finally, all the MR images were now in the
same template space and had the same intensity range

## [Freesurfer output Feature Extraction for Regression Task](Feature%20Extraction%20for%20Regression)
The extraced features and steps to extract features from output files from ADNI dataset is in ```Feature Extraction for Regression``` folder. The same steps can be followed for any T1-weighted dataset

## [Freesurfer output Processing for GCNs](Cortical%20Thickness%20Graph%20Creation) 
For GCNs we resample all the Freesurfer thickness outputs to the fsaverage brain so that all the samples have same adjacency matrix. The resulting adjacency matrix will be 163842 X 163842 and the cortical thickness file will be 163842 X n where n is the number of samples. 


