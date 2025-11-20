Currently testing if we can get the OCEAN file to run with DDM on. 

Current run script is: run_cctm_20190220_20190227_MACS12km_DDMon.csh


Build is: BLD_CCTM_v55_DDM3D_gcc_cb6r5_ae7_aq_m3dry_debug

CMAQ_Control_Misc file was edited to reduce number of species output for AELMO, tried suggested list of common species, PM, "ALL", and "DEFAULT" (first two are commenedted out - see lines 108 / 109)

CCTM/src/util/util/CMAQ_Control_Misc_reduced_aelmo_output_2025-11-06.nml

*Note this file is copied to builds folder during build - it will be necessary to rerun bldit_cctm if any changes are made. The current bldit_cctm folder points to CMAQ_Control_Misc_reduced_aelmo_output_2025-11-06.nml

 ****
ERRORS
****

Tried running with ‘ALL’ or ‘DEFAULT’ variables in AELMO, and also set ACONC in the run script to ‘ALL’ in case they need to be consistent (there isn’t a ‘DEFAULT’ option for ACONC). 

Reading the log seems to be something with the path for writing the CTM_CONC_1 file?


     *** ERROR ABORT in subroutine OPASENS on PE 000
     Number of variables don't match file:    666   654

The error in CTM_LOG_007.txt occurs because the model cannot retrieve the description for the file CTM_CONC_1, which is required by the sensitivity analysis routine (OPASENS). The log shows:
*** ERROR ABORT in subroutine OPASENS on PE 007
Could not get CTM_CONC_1 file description
 
