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

Script_R2P1_PALM filtering and analyis (PALM data filtering and first part of the analysis):
- Input: ROIs obtained from "Script_R1_ROI_mod"
- Input: Elyra_Table_Example
- Output: Channel_#_updatedtableX.txt (Elyra table drifted according to the ROIs)
- Output: AreaListX.RData (ROIs - both channels give the same output)
- Output: Channel_#_table_drifted_filtered.txt (Channel_#_table_drifted_filtered Example)
- Output: Channel_#_updatedtableX_partial_analysis.txt (Channel_#_updatedtableX_partial_analysis Example)

Channel_#_updatedtableX and Channel_#_table_drifted_filtered example: (first 13 columns are the same as the "Elyra_Table_example" - they differ for the extra lines at the end (lines necessary for importing in via ZEN_Black on the Elyra))
- CellName: ROI file name (R.Cell*.txt)
- CellDiameter: Diameter of the ROI in nm
- CellArea: Area of the ROI in square nm

Channel_#_updatedtableX_partial_analysis example: (first 16 columns are the same as Channel_#_updatedtableX.txt)
- Clust50Name: Name of the cluster to which the localization belongs (threshold 50 nm)
- Clust50Size: Number of localizations belonging the same cluster (threshold 50 nm)
- LocalDensity: Number of localizations within a square area of side 50 nm centered on the localization
- Clust40Name: Name of the cluster to which the localization belongs (threshold 40 nm)
- Clust40Size: Number of localizations belonging the same cluster (threshold 40 nm)
- Clust30Name: Name of the cluster to which the localization belongs (threshold 30 nm)
- Clust30Size: Number of localizations belonging the same cluster (threshold 30 nm)
- Clust20Name: Name of the cluster to which the localization belongs (threshold 20 nm)
- Clust20Size: Number of localizations belonging the same cluster (threshold 20 nm)
- Clust10Name: Name of the cluster to which the localization belongs (threshold 10 nm)
- Clust10Size: Number of localizations belonging the same cluster (threshold 10 nm)
- Clust5Name: Name of the cluster to which the localization belongs (threshold 5 nm)
- Clust5Size: Number of localizations belonging the same cluster (threshold 5 nm)
- Field: Name of the Field of view
- ClustMaxDist50: Maximum distance between localizations belonging to the same cluster (threshold 50 nm)
- ClustMaxDist40: Maximum distance between localizations belonging to the same cluster (threshold 40 nm)
- ClustMaxDist30: Maximum distance between localizations belonging to the same cluster (threshold 30 nm)
- ClustMaxDist20: Maximum distance between localizations belonging to the same cluster (threshold 20 nm)
- ClustMaxDist10: Maximum distance between localizations belonging to the same cluster (threshold 10 nm)
- ClustMaxDist5: Maximum distance between localizations belonging to the same cluster (threshold 5 nm)
- Unique50: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 50 nm)
- Unique40: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 40 nm)
- Unique30: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 30 nm)
- Unique20: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 20 nm)
- Unique10: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 10 nm)
- Unique5: Identifies unique clusters (use filter parameter "yes" to avoid using the same cluster twice while analysing)(threshold 5 nm)
- ClosestNeigh: Distance from closest neighbour (nm)
- ClosestNeighIndex: Index of the closest neighbour
- AvgDens50: Average LocalDensity within the cluster (threshold 50 nm)
- MaxDens50: Maximum LocalDensity within the cluster (threshold 50 nm)
- MinDens50: Minimum LocalDensity within the cluster (threshold 50 nm)
- AvgDens40: Average LocalDensity within the cluster (threshold 40 nm)
- MaxDens40: Maximum LocalDensity within the cluster (threshold 40 nm)
- MinDens40: Minimum LocalDensity within the cluster (threshold 40 nm)
- AvgDens30: Average LocalDensity within the cluster (threshold 30 nm)
- MaxDens30: Maximum LocalDensity within the cluster (threshold 30 nm)
- MinDens30: Minimum LocalDensity within the cluster (threshold 30 nm)
- AvgDens20: Average LocalDensity within the cluster (threshold 20 nm)
- MaxDens20: Maximum LocalDensity within the cluster (threshold 20 nm)
- MinDens20: Minimum LocalDensity within the cluster (threshold 20 nm)
- AvgDens10: Average LocalDensity within the cluster (threshold 10 nm)
- MaxDens10: Maximum LocalDensity within the cluster (threshold 10 nm)
- MinDens10: Minimum LocalDensity within the cluster (threshold 10 nm)
- AvgDens5: Average LocalDensity within the cluster (threshold 5 nm)
- MaxDens5: Maximum LocalDensity within the cluster (threshold 5 nm)
- MinDens5: Minimum LocalDensity within the cluster (threshold 5 nm)
- v63: empty column

Script_R2P2_OpticsOptimization (Clustering via Optics):
- Input: Channel_#_updatedtableX_partial_analysis.txt (Channel_#_updatedtableX_partial_analysis Example)
- Output: Channel_#_updatedtableX_partial_analysis_clustering.txt (Channel_#_updatedtableX_partial_analysis_clustering Example)

Channel_#_updatedtableX_partial_analysis_clustering example: (first 63 columns are the same as Channel_#_updatedtableX_partial_analysis.txt)
- 

Script_R3_CBC_calculation_and_plot: Calculate the coordinate-based colocalization values of single-molecule localization data (CBC)
fileR3
- Input: AreaListX.RData (ROIs)
- Input: "Channel_#_flagella_drifted_filtered.txt" (PALM_filtering_output example)(one input for channel)
- Output: pamCBC.txt (table including the Calculation of the rank correlation coefficient (Spearman) "S" and of the colocalization value for the PAmCherry molecules respective to mNeonGreen "Ca" )
- Output: neoCBC.txt (table including the Calculation of the rank correlation coefficient (Spearman) "S" and of the colocalization value for the mNeonGreen molecules respective to PAmCherry "Ca" )
- Output: PLOTS
