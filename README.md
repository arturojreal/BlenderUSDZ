# Blender UDSZ File Import-Export Add-On

USDZ file Import-Export add-on for [Blender](https://www.blender.org) that provides a simple method for importing and exporting models for use in Augmented Reality applications.


## Installation

1. Download `io_export_usdz.zip` file from the root of this repository
2. Open Blender 2.8  and Go to `Edit -> Preferences...`
3. In Preferences select `Add-ons` on the left-hand menu and then select the `Install` button on the top right corner of the window
4. Navigate to and select the `io_export_usdz.zip` file from Step 1
5. Select the check mark next to `Import-Export: UDSZ` format to enable the add-on 


## Usage

Always be sure to save your work before using this tool.
This tool will attempt to export the currently selected objects in the Blender scene. 
The tool can be found in Blender under `File -> Export -> USDZ (.usdz)`.
When selected, the add-on will present the usual file export window, along with some options on the right-side toolbar.
Options selected and the size and complexity of the selected objects will affect the amount of time it takes to export a USDZ file.


## Add-on Options

### Import Options

Import Materials - By selecting this option, the add-on will attempt to import materials associated with objects.

### Export Options

Export Materials - The exporter will export object materials as USD Principled shader materials which share many of the same properties as the Principled BSDF shader for Eevee and Cycles in Blender. Mix and Add shader nodes are not supported yet in this add-on.

Export Animations - When selected, the active object/bone animation will be exported to the USDZ file. Currently, any animations are baked per-frame.

Bake Textures - When enabled, any textures associated with materials will be baked out to image files that will be bundled into the USDZ file. Currently, the add-on will automatically switch to Cycles to bake images, which could take a significant amount of time. This option is ignored if `Export Materials` is unchecked.

Bake AO - This options bakes ambient occlusion textures that are applied to the USD Principled shader materials in the USDZ file. Enabling this option can add a significant amount of time to export. This option is ignored if `Export Materials` is unchecked.

Samples - This option determines the number of samples used in baking the ambient occlusion textures. A higher number generates higher-quality occlusion textures with added time to export. This option is ignored if either `Export Materials` or `Bake AO` options are unchecked.

Scale - This value is used to scale the objects exported to the USDZ file.

Use USDZ Converter Tool - By selecting this option, the add-on will export a .usda file that will be converted to USDZ by the external USDZ Czonverter Tool bundled with Xcode. ```Note that the USDZ Converter has been deprecated from the current version of Xcode and this option will no longer work.```

## Notes

This add-on has only been tested to work on macOS and there are no guarantees that it will work on Windows or Linux.

The generated binary USD file used in the exported USDZ file could potentially be incompatible with some Augmented Reality applications. In these cases, it is recommended to export the text version of a USD file by adding the ".usda" extension to the exported file's name. Then, use the `usdconvert` tool in `usdpython` to generate the final USDZ file.

The import functionality is currently limited to simple static models with no animations.

