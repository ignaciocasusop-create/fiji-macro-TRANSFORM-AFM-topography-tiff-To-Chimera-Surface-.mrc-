# fiji-macro-TRANSFORM-AFM-topography-tiff-To-Chimera-Surface-.mrc-
fiji-macro TRANSFORM AFM topography (tiff) To Chimera Surface (.mrc)

Manuscript 
Stepwise assembly and mechanical stability of nsP3 Helical Scaffolds in Chikungunya Virus
Natalia Martín-González1, 2,3, Andrei Karpov1,2,3, Juan Reguera2,3 and Ignacio Casuso1
1Aix-Marseille Université, INSERM, DyNaMo U1325, Turing centre for living systems, Marseille, France
2Aix-Marseille Université, CNRS, AFMB UMR 7257, Turing centre for living systems, Marseille, France
3INSERM, Viral Macromolecular Complexes team, INSERM U1324, Marseille, France

To compare the HS-AFM topography to the cryo-EM structural data, a custom-made code was was implemented using the macro coding language of free available software and plugins (Fiji is just ImageJ, the version 1.54f 64-bit works correctly). The procedure is the following: 1) the HS-AFM movie was opened in Fiji as .tif file. 2) the frame of interest is selected. 3) the code of the Macro01_AFM2Chimera_ (available in Suppl. Information) is run. 3) the code Macro02_AFM2Chimera_ (available in Suppl. Information) is run. 5) The file created by the Macro02_AFM2Chimera is opened in USCF Chimera (version 1.13.1 works correctly), the map values are inverted, a volume filter of 2 applied, and the range adjusted until a full surface obtained. Finally, the scale bar and the voxel coordinates are used to ajust the dimensions of the molecules in the USCF Chimera surface visualization to that of the HS-AFM topography. 6) The resulting surface map is saved in .mrc format.
