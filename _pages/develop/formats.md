---
title: Adding new formats
section: Extend:Development:Guides
---

Before an image can be analyzed, it needs to be opened properly. The way scientific image data can be stored varies wildly - with custom formats as numerous as the different brands and models of instruments used in their acquisition. Therefore, supporting a wide variety of formats is critical to the success of an image analysis platform like ImageJ.

[ImageJ2](/software/imagej2) provides a comprehensive solution to the issue of data formats in the form of [SCIFIO](/libs/scifio) data format plugins. [SCIFIO](/libs/scifio), the SCientific Image Format Input and Output library, is a flexible framework for image format support. To get started writing SCIFIO formats:

-   Check out the [SCIFIO tutorials](https://github.com/scifio/scifio-tutorials/tree/master/core/src/main/java/io/scif/tutorials/core).
-   Look at simple [existing formats](https://github.com/scifio/scifio/blob/scifio-0.24.0/src/main/java/io/scif/formats/BMPFormat.java) for a starting point.

## ImageJ 1.x format handling

With the original [ImageJ](/software/imagej), a special [HandleExtraFileTypes](https://imagej.nih.gov/ij/plugins/file-handler.html) plugin exists that can be modified to support new data formats—but it has some significant disadvantages:

-   It only provides limited extensibility: there can only be one `HandleExtraFileTypes` installed into ImageJ at a time, so all desired modifications to the plugin must be somehow combined. This makes it impossible to, for example, ship a different `HandleExtraFileTypes` on two different ImageJ [Update Sites](/update-sites) and have both additions be available in the same installation.
-   Data formats added in this manner cannot override or extend ImageJ's built in support for certain file formats. In particular, ImageJ supports only a subset of the TIFF specification, and this issue cannot be circumvented via `HandleExtraFileTypes` modifications.

## See also

-   [Bio-Formats](/formats/bio-formats)


