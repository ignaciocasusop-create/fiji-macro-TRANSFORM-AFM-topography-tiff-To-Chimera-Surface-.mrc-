# fiji-macro-TRANSFORM-AFM-topography-tiff-To-Chimera-Surface-.mrc-
fiji-macro TRANSFORM AFM topography (tiff) To Chimera Surface (.mrc)

Manuscript 
Stepwise assembly and mechanical stability of nsP3 Helical Scaffolds in Chikungunya Virus
Natalia Martín-González1, 2,3, Andrei Karpov1,2,3, Juan Reguera2,3 and Ignacio Casuso1
1Aix-Marseille Université, INSERM, DyNaMo U1325, Turing centre for living systems, Marseille, France
2Aix-Marseille Université, CNRS, AFMB UMR 7257, Turing centre for living systems, Marseille, France
3INSERM, Viral Macromolecular Complexes team, INSERM U1324, Marseille, France

To compare the HS-AFM topography to the cryo-EM structural data, a custom-made code was was implemented using the macro coding language of free available software and plugins (Fiji is just ImageJ, the version 1.54f 64-bit works correctly). The procedure is the following: 1) the HS-AFM movie was opened in Fiji as .tif file. 2) the frame of interest is selected. 3) the code of the Macro01_AFM2Chimera_ (available in Suppl. Information) is run. 3) the code Macro02_AFM2Chimera_ (available in Suppl. Information) is run. 5) The file created by the Macro02_AFM2Chimera is opened in USCF Chimera (version 1.13.1 works correctly), the map values are inverted, a volume filter of 2 applied, and the range adjusted until a full surface obtained. Finally, the scale bar and the voxel coordinates are used to ajust the dimensions of the molecules in the USCF Chimera surface visualization to that of the HS-AFM topography. 6) The resulting surface map is saved in .mrc format.


//------------------------------------------------------------------
// Macro 01 — AFM-to-Chimera conversion
// The following macro converts the selected HS-AFM frame into the intermediate format required for the subsequent conversion step.

// ## Macro01_AFM2Chimera_
// credits AFM2Chimera:
// code by Ignacio CASUSO, INSERM, Marseille 2023
// email: ignacio.casuso@inserm.fr
// 


waitForUser("FIND and show the frame of interest, next click OK");
rename("InputStack");
run("Duplicate...", " ");
selectImage("InputStack");
close();
selectImage("InputStack-1");
run("32-bit");
run("Subtract Background...", "rolling=256 disable");
setOption("ScaleConversions", true);
run("8-bit");
run("Multiply...", "value=0.9");
run("8-bit");
rename("RawImage");
stepsize=1;
i_max=255/stepsize;
for(i = 1;i<i_max;i++){ 
maxlevel=i*stepsize;	
run("Duplicate...", " ");
setThreshold(0, maxlevel);
setOption("BlackBackground", false);
run("Convert to Mask");
run("Outline");
//run("32-bit");
//run("Manual Threshold...", "min=2 max=260");
//run("NaN Background");
selectWindow("RawImage");
}
close();
run("Images to Stack");
waitForUser("FIND the number of slide of the substrate and run SurfaceTomography_AFM_Image_02_ ");
Macro 02 — AFM-to-Chimera conversion
The following macro generates the surface-map file used for visualization in UCSF Chimera.

//------------------------------------------------------------------
// ## Macro02_AFM2Chimera_
// credits AFM2Chimera:
// code by Ignacio CASUSO, INSERM, Marseille 2023
// email: ignacio.casuso@inserm.fr
// 
substrate=getNumber("WRITE the number of slide JUST ABOVE the substrate to fill the SUBSTRATE", 0);
setSlice(substrate); 
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Previous Slice [<]");
run("Add...", "value=255 slice");
run("Invert", "stack");
rename("Tiff_VolumeStack_");
waitForUser("save the stack as .tif in a folder and open it with Chimera");
saveAs(".tif");
