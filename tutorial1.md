<div class="node clear-block">

<div class="content">

Getting Started
===============

Multiple Sequence Alignment Viewer (MSA) is a web application that helps
to visualize multiple alignments created by different msa programs
(MUSCLE, CLUSTAL, etc.) or database search results (like BLAST) in
multiple alignment view.

To see all MSA features go to the [Multiple Sequence Alignment Viewer
application](/projects/msaviewer/) page.

MSA home page shows a number of protein and DNA alignment examples.

The **Getting Started** tutorial will take you through the steps showing
how to upload data into MSA viewer and perform basic operations with
alignment including alignment navigation, set master and coloration
methods.

Please download the
[carbohydrate\_kinase\_FGGY.aln](ftp://ftp.ncbi.nlm.nih.gov/toolbox/gbench/samples/carbohydrate_kinase_FGGY.aln)
data file (to be used in the tutorial).

Step 1: Alignment uploading {#step1}
---------------------------

Click the **Upload** button on [MSA home page](/projects/msaviewer/).
**Upload Data** dialog opens showing the Data Source list.\
 There are a few data types can be uploaded into MSA viewer:

-   BLAST Results
-   Data File
-   URL
-   Text

[![upload data
dialog](/core/assets/msaviewer/images/upload-data-dialog.png)](/@msaviewer/images/upload-data-dialog.png)

We will upload the Data File with protein alignment in FASTA format
created by MUSCLE program. Select the Data File and browse to
carbohydrate\_kinase\_FGGY.aln file. Click on **Upload** button in the
**Upload Data** dialog, wait for data uploading, and click on **Close**
button.

Observe multiple alignment uploaded into MSA viewer.

[![multiple
alignment](/core/assets/msaviewer/images/multiple-alignment.png)](/@msaviewer/images/multiple-alignment.png)

Step 2: Select sequences to see alignment information {#step2}
-----------------------------------------------------

Point the mouse cursor to any sequence in alignment. A tooltip will open
showing the sequence ID and other information about the aligned
position.

[![tooltip](/core/assets/msaviewer/images/tooltip.png)](/@msaviewer/images/tooltip.png)

The tooltip can be pinned by clicking on the pin icon in the left corner
of the tooltip.

In MSA view **Descriptions** column shows sequence accession numbers.

*Note: MSA viewer ignores gi(s) if there are both (gi)s and accession
IDs in sequence deflines.*

There are also the **Seq Start** and **Seq End** columns and the
**Organism** column.

*Note: currently information about organism is present for BLAST RID,
ID, and Trace assembly alignments visualization only.*

[![columns
1](/core/assets/msaviewer/images/columns1.png)](/@msaviewer/images/columns1.png)

[![columns
2](/core/assets/msaviewer/images/columns2.png)](/@msaviewer/images/columns2.png)

Step 3: Alignment zooming and navigation (by left/right arrows and dragging) {#step3}
----------------------------------------------------------------------------

To navigate an alignment use the Navigation panel or the Tools menu at
the right upper corner.

Tools menu can be open by right clicking anywhere in alignment area.

[![tools
menu](/core/assets/msaviewer/images/tools-menu.png)](/@msaviewer/images/tools-menu.png)

In navigation panel click on the **+** icon next to the zoom slider and
observe changes of the sequence color.

[![navigation
panel](/core/assets/msaviewer/images/navigation-panel.png)](/@msaviewer/images/navigation-panel.png)

Use **left/right arrows** to move to left/right parts of the alignment.
Use mouse to drag alignment left and right.

You can also click on the **ATG** icon to zoom in to a sequence level.

[![sequence level
zoom](/core/assets/msaviewer/images/sequence-level-zoom.png)](/@msaviewer/images/sequence-level-zoom.png)

Step 4: Coloring methods {#step4}
------------------------

Different methods can be used to color alignment. To see available
methods open the **Tools** menu (at the right upper corner of the
alignment or on the right click) and select the **Coloring** option.

[![rasmol amino acid
colors](/core/assets/msaviewer/images/rasmol-amino-acid-colors.png)](/@msaviewer/images/rasmol-amino-acid-colors.png)

Rasmol Amino Acid Colors are the default colors for a protein alignment.
Select any other methods (for example Frequency Based Differences) and
observe the color being changed.

[![frequency based
differences](/core/assets/msaviewer/images/frequency-based-differences.png)](/@msaviewer/images/frequency-based-differences.png)

*Note: method “Show Differences” highlights differences observed from
the master sequence in an alignment. In order to see any coloration with
this scheme, you must select a master sequence first.*

Step 5: Set/Unset master sequence using right click menu {#step5}
--------------------------------------------------------

Zoom out to 0% using Zoom slider to see the whole length of alignment.
Observe that uploaded alignment doesn’t have any master sequence set
(the length of the alignment is 785 amino acids).

[![uploaded
alignment](/core/assets/msaviewer/images/uploaded-alignment.png)](/@msaviewer/images/uploaded-alignment.png)

To see how sequences can be align to the particular sequence in the
alignment this sequence can be set as a master. Let us set master to the
sequence with accession number **Q9LBQ3.1** shown in Descriptions
column. To set master, point cursor to this sequence (this action
selects sequence), open the right click menu, and select the **Set
master** option. Observe that now **Q9LBQ3.1** sequence is the first
sequence in the alignment and the length of the alignment is 563 amino
acids.

[![set master
1](/core/assets/msaviewer/images/set-master1.png)](/@msaviewer/images/set-master1.png)

[![set master
2](/core/assets/msaviewer/images/set-master2.png)](/@msaviewer/images/set-master2.png)

Point cursor to any sequence again and open right click menu, observe
that now it has **Set master** and **Unset master** options. You can set
any sequence as a master or unset maser and observe that order of
sequences was restored.

</div>

</div>

<div id="shared-content-1" nid="4988">

Table of Contents
-----------------

-   [Multiple Sequence Alignment Viewer
    application](/projects/msaviewer/)
-   [Documentation home](/tools/msaviewer/)
-   General
    -   [About](/tools/msaviewer/about/)
    -   [MSA Viewer Embedding API](/tools/msaviewer/embedding-api/)
    -   [Release Notes](/tools/msaviewer/release-notes/)
-   Help
    -   [Frequently Asked Questions](/tools/msaviewer/faq/)
    -   [Video Tutorials](/tools/msaviewer/video/)
    -   [Legend](/tools/msaviewer/legend/)
-   Demo Pages
    -   [Static Embedding](/projects/msaviewer/demo_static.html)
    -   [Dynamic Embedding](/projects/msaviewer/demo_dynamic.html)
    -   [Interaction with Sequence
        Viewer](/projects/msaviewer/demo_sv.html)
    -   [Event Handling](/projects/msaviewer/demo_events.html)
    -   [Coloring](/projects/msaviewer/demo_coloring.html)
    -   [Alignment Coordinate
        Transformation](/projects/msaviewer/demo_mapping.html)
-   Tutorials
    -   [Getting Started](/tools/msaviewer/tutorial1)
-   Other Resources
    -   [Genome Workbench](/tools/gbench/)
    -   [Sequence Viewer](/projects/sviewer/)
    -   [Tree Viewer](/projects/treeview/)

</div>
