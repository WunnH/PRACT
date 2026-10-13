# PRACT Reproducibility Parameters

## Imaging and voxel size

(1) Nanjing Brain Hospital STN-DBS clinical cohort (NBH-STN-DBS)
The voxel spacing of the T1WI planning space was 1.0000 × 0.9375 × 0.9375 mm, corresponding to a one-voxel displacement of approximately 0.94–1.00 mm along the principal axes.
(2) Lead-Tutor
The voxel spacing of the T1WI planning space was 0.9766 × 0.9766 × 1.0000 mm, corresponding to a one-voxel displacement of approximately 0.98–1.00 mm along the principal axes.
## Spatial mapping

PRACT used the patient-specific T1WI planning space as the unified anatomical reference. T2WI-derived STN and red-nucleus masks were mapped to the T1WI planning space, and SWI was mapped to the same planning grid when available.

Spatial mapping used the existing NIfTI affine/header geometry. Intensity images were resampled using linear interpolation, whereas binary masks were resampled using nearest-neighbour interpolation.

Registration accuracy was not independently quantified in the present cohort.

## Perturbation scenarios

For cases with vessel, sulcus, and ventricle information, the uncertainty set comprised 19 evaluation scenarios: one nominal scenario and 18 perturbed scenarios. One voxel corresponded to 1.0000 mm along voxel axis 0 and 0.9375 mm along voxel axes 1 and 2.

| Scenario | Operation | Voxel magnitude | Physical magnitude (mm) |
|---|---|---:|---|
| nominal | Unperturbed masks and target | 0 | 0 |
| vessel_dilate_1voxel | Vessel boundary broadening | 1 voxel | Axis-dependent: 1.0000 or 0.9375 |
| sulcus_erode_1voxel | Sulcus-mask erosion | 1 voxel | Axis-dependent: 1.0000 or 0.9375 |
| sulcus_dilate_1voxel | Sulcus-mask dilation | 1 voxel | Axis-dependent: 1.0000 or 0.9375 |
| ventricle_erode_1voxel | Ventricle-mask erosion | 1 voxel | Axis-dependent: 1.0000 or 0.9375 |
| ventricle_dilate_1voxel | Ventricle-mask dilation | 1 voxel | Axis-dependent: 1.0000 or 0.9375 |
| combined_conservative_mask_dilation | Simultaneous dilation of all available risk structures | 1 voxel per mask | Axis-dependent |
| target_shift_x_plus_1voxel | Target shift along +voxel axis 0 | 1 voxel | 1.0000 |
| target_shift_x_minus_1voxel | Target shift along −voxel axis 0 | 1 voxel | 1.0000 |
| target_shift_y_plus_1voxel | Target shift along +voxel axis 1 | 1 voxel | 0.9375 |
| target_shift_y_minus_1voxel | Target shift along −voxel axis 1 | 1 voxel | 0.9375 |
| target_shift_z_plus_1voxel | Target shift along +voxel axis 2 | 1 voxel | 0.9375 |
| target_shift_z_minus_1voxel | Target shift along −voxel axis 2 | 1 voxel | 0.9375 |
| combined_dilation_target_shift_x_plus_1voxel | Simultaneous dilation of all available risk structures and target shift along +voxel axis 0 | 1 voxel per mask and target shift | Axis-dependent; target shift: 1.0000 |
| combined_dilation_target_shift_x_minus_1voxel | Simultaneous dilation of all available risk structures and target shift along −voxel axis 0 | 1 voxel per mask and target shift | Axis-dependent; target shift: 1.0000 |
| combined_dilation_target_shift_y_plus_1voxel | Simultaneous dilation of all available risk structures and target shift along +voxel axis 1 | 1 voxel per mask and target shift | Axis-dependent; target shift: 0.9375 |
| combined_dilation_target_shift_y_minus_1voxel | Simultaneous dilation of all available risk structures and target shift along −voxel axis 1 | 1 voxel per mask and target shift | Axis-dependent; target shift: 0.9375 |
| combined_dilation_target_shift_z_plus_1voxel | Simultaneous dilation of all available risk structures and target shift along +voxel axis 2 | 1 voxel per mask and target shift | Axis-dependent; target shift: 0.9375 |
| combined_dilation_target_shift_z_minus_1voxel | Simultaneous dilation of all available risk structures and target shift along −voxel axis 2 | 1 voxel per mask and target shift | Axis-dependent; target shift: 0.9375 |


**The perturbation configuration included erosion and dilation of the sulcal and ventricular masks, one-voxel boundary broadening of the vascular risk regions, simultaneous dilation of all available risk structures, six axis-wise target-position shifts, and six compound scenarios combining simultaneous dilation of all available risk structures with each axis-wise target-position shift.**

## Candidate trajectory generation

For each predefined STN target, candidate directions were sampled outward toward the cortical surface in the patient-specific T1WI planning space. The intersections with the cortical surface defined the initial cortical entry candidates.

Candidate trajectories were retained when they satisfied the predefined angular constraints of 10°–25° relative to the sagittal plane and 50°–65° relative to the axial plane. A coronal-suture-based entry-zone constraint was subsequently applied, retaining cortical entry candidates located within 20 mm anterior to the estimated coronal-suture reference.

Each retained cortical entry point was connected to the predefined STN target to form a straight-line candidate trajectory.

