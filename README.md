# ParB clustering / protein profiling

Available Files:

Elyra_Table_example: 
- Index
- First Frame: Frame at which an event firstly appear
- Number Frames: (relevant only when grouping)
- Frame Missing: (relevant only when grouping)
- Position X [nm]: (0 to 51200)
- Position Y [nm]: (0 to 51200)
- Precision [nm]
- Number Photons
- Background Variance
- Chi square
- PSF half width [nm]
- Channel: relevant only for dual color
- Z Slice: relevant only for Z stacks 

Script_R1_ROI_mod (ROI modification script):
- Input: ROIs obtained via Fiji -> need to be named Cell*.txt
- Output: ROIs ready to be used for "Script_R2_PALM filtering" script -> R.Cell*.txt

Script_R2_PALM filtering (PALM data filtering):
- Input: ROIs obtained from "Script_R1_ROI_mod"
- Input: Elyra_Table_Example
- Output: Channel_#_updatedtableX (Elyra table drifted according to the ROIs - Channel specific)
- Output: AreaListX.RData (ROIs - both channels give the same output)
- Output: Channel_#_flagella_drifted_filtered.txt (PALM_filtered_output example)

PALM_filtering_output example: (first 13 columns are the same as the "Elyra_Table_example")
- CellName: ROI file name (R.Cell*.txt)
- CellDiameter: Diameter of the ROI in nm
- CellArea: Area of the ROI in square nm

Script_R3_CBC_calculation_and_plot: Calculate the coordinate-based colocalization values of single-molecule localization data (CBC)

- Input: AreaListX.RData (ROIs)
- Input: "Channel_#_flagella_drifted_filtered.txt" (PALM_filtering_output example)(one input for channel)
- Output: pamCBC.txt (table including the Calculation of the rank correlation coefficient (Spearman) "S" and of the colocalization value for the PAmCherry molecules respective to mNeonGreen "Ca" )
- Output: neoCBC.txt (table including the Calculation of the rank correlation coefficient (Spearman) "S" and of the colocalization value for the mNeonGreen molecules respective to PAmCherry "Ca" )
- Output: PLOTS
