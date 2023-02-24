# EPR_brain_fitting

Semi-automatic EPR spectra processing of brain samples using EasySpin functions.

## spectra_processing.m
Use the 'spectra_processing.m' file for the general processing of EPR spectra. This script is divided into 4 steps:
  - 1) EPR data load
  - 2) Baseline correction
  - 3) Fitting
  - 4) Analysis

## baseCorr1.m
Baseline correction by defining initial, end and middle points as 'zero' signal. The function uses these points to fit an n-order polynomial. The fitted polynomial is, then, subtracted from the raw spectrum

## baseCorr2.m
Baseline correction by defining the end points as 'zero' signal. The function calculates a linear baseline and subtracts from the raw spectra, and afterwards looks into the 2nd integral spectrum, checking if a plateau was reached. If not, then it changes the slope of the linear baseline by a small amount and repeats the process in an iterative way until a plateau is reached on the 2nd integral spectrum. 

## smooth_fft.m
Performs a smoothing of the spectrum by employing a Fast Fourier Transform filter. The cutoff frequency is defined according to the number of points of the input function (similar to the Origin function)

## epr_brain_fitting.m
Takes the inputs and performs the fitting and the simulation of the peak of interest. The function uses the EasySpin function 'pepper' to open the GUI for the fitting, and after a good fitting is reached the user should export the best fit parameters to Matlab's workspace.
After the bet fit parameters have been exported to Matlab's workspace, then the function takes these values and perform a simulation over the full range and calculates the multiplicative factor in order for the simulated peak to best agree with experimental spectrum.
