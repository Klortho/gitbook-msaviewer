
NCBI Multiple Sequence Alignment Viewer Embedding API
=====================================================

------------------------------------------------------------------------

Document Update Date: 06/27/2016

MSA Viewer Revision: 1.0

Contact: sviewer-service AT ncbi.nlm.nih.gov

------------------------------------------------------------------------

Introduction
------------

The NCBI Multiple Sequence Alignment Viewer (MSAV) is a general purpose
tool for viewing multiple alignments of biological sequences. It can be
embedded in a wide variety of web pages and with a large number of
options. This document serves as a launching point to understand how to
embed the Multiple Sequence Alignment Viewer in any context. For
purposes of standardization in this document, all links presented
include the common refrain <https://www.ncbi.nlm.nih.gov>.

For questions please contact: sviewer-service AT ncbi.nlm.nih.gov

Additional documentation can be found at:
<http://www.ncbi.nlm.nih.gov/tools/msaviewer>

Including Multiple Sequence Alignment Viewer into a web page {#including}
------------------------------------------------------------

The Multiple Sequence Viewer is a component which can be embedded on
internal NCBI as well as external Web page.

The Viewer is implemented using ExtJS JavaScript library version 5.0.1.
There are some rules to follow when including the Viewer as a component
on a page.

1.  There is no need to declare or load ExtJS css files or js scripts.
    MSAV dynamically loads everything it needs from
    www.ncbi.nlm.nin.com website. On the other hand if ExtJS scripts are
    declared/loaded before multialign.js declaration MSAV omits their
    loading so this allows an embedding application to use a specific
    edition of the library (compatible to version 5.0.1). The following
    example demonstrate how to declare MSAV script:\

    &lt;script type="text/javascript"\

    src="https://www.ncbi.nlm.nih.gov/projects/msaviewer/js/multialign.js"&gt;&lt;/script&gt;

2.  If an embedding application does not create MSAV instances
    dynamically MSAV application finds appropriate MultiAlignViewerApp
    declarations and create instances automatically (with data loading).
    For this the ‘div’ element should have class='MultiAlignViewerApp'
    and extra attribute ‘data-autoload’, and ‘a’ element inside ‘div’
    with ‘href’ attribute containing MSA Viewer parameters. An example
    is:

    &lt;div id='some-id' class='MultiAlignViewerApp' data-autoload&gt;\
         &lt;a href='?embedded=true&id=…'&gt;&lt;a&gt;\
     &lt;/div&gt;

    Please pay attention to the question mark at the beginning of
    ‘href’ argument. It is a syntax dictated by Web browsers and
    is obligatory.

    Do not use this method if the Multiple Sequence Alignment Viewer div
    is initially hidden - it breaks all the logic as the Viewer needs to
    have real coordinate for proper rendering. Use method from point 3
    to instantiate Multiple Sequence Alignment Viewer dynamically.

3.  If an embedding application needs to create MSAV instances
    dynamically the following example demonstrates how to declare them
    and initiate MSAV instances creation and loading:

    &lt;div id=’msav1’&gt;&lt;/div&gt;\
     ...\
     &lt;script type='text/javascript'&gt;\
     MultiAlignViewOnReady(function()\
     { var app = new MultiAlignView.App(‘msav1’);
    app.load(‘embedded=true&id=…’); }\
     );\
     &lt;/script&gt;

4.  Function MultiAlignViewOnReady(callback, \[scope\]) is designed to
    prevent MSAV usage before MultiAlignView class is initialized.

    Parameters:\
     **callback** - user callback function\
     **scope** - callback function scope (if necessary)

Data Formats Supported {#dataformats}
----------------------

NCBI ASN.1 data containing alignment objects.

BLAST RID – request id of submission of a sequence to NCBI BLAST
service.

MUSCLE – external format (to be implemented), result of run of MUSCLE
tool (<https://www.drive5.com/muscle/>).

Multiple Sequence Alignment Viewer Parameters {#parameters}
---------------------------------------------

Parameters may be passed to Multiple Sequence Alignment Viewer by
putting them in the included &lt;a href=''&gt; link tag within the MSA
Viewer &lt;div&gt; tag.

**appname** – it’s a way to identify who is using the component. It’s a
mandatory parameter which should be unique for your application. If you
plan to embed MSA Viewer on your page please email us at sviewer-service
AT ncbi.nlm.nih.gov with suggested load so that we can plan our resource
allocation.

One of the following parameters MUST be present as a source of alignment
data:\
 **id** – id of the sequence which has alignment data, can be gi or
accession\
 **rid** – BLAST RID for already finished job\
 **url** – URL pointing to the data file\
 **key** – key for the data stored at NCBI after user data upload.
Usually visible in URL produced by applications\
 **master** – the id of a row to be selected as master\
 **scoring** – scoring method, to be implemented

There are two alternative ways to set a visible range for the view:\
 **f** – from, 1-based position of the beginning of the view\
 **t** – to, 1-based position of the end of the view\
 or\
 **v** – view range, 1-based range in the format from:to

Events Sent by MSAV Instance {#events}
----------------------------

An application that uses MSAV can subscribe to events that MSAV will
send in case of a user interaction with MSAV. Here is the list of
supported events with parameters passed in each event.

**'graphical\_image\_loaded'** - fired when graphical image is loaded to
view\
 view – view object of the just loaded image

**'visible\_range\_changed'** - fired when visible range is changed (for
example, zoom or shift)\
 range – array with \[from, to, len\] of the sequence or alignment
visible

**'selection\_changed'** - fired when the selection is changed\
 rows – array of row ids selected

**'master\_changed'** - fired when the master is set/unset\
 row\_id – row id of new master or null if master is unset

**'coloring\_changed'** - fired when coloring of the alignment is
changed\
 coloring – what specific coloring is applied

Functions
---------

**MultiAlignView.App.getApps()** – get array with all app objects

**MultiAlignView.App.findAppByIndex(num)** – find an app by its ordinal
number

**MultiAlignView.App.findAppByDivId(id)** – find an app instantiated in
div with given id

App Methods
-----------

**getRows(fSelected)** – get array of all or only selected rows

**selectRow(row\_id, fSelect)** – select or unselect row with row\_id

**getMaster** – get currently set master or null if unset

**setMaster(row\_id)** – set master

**getRowInfo(row\_id)** – returns object with following fields (can be
extended in the future):\
 **id** – sequence id for the row\
 **start** – start of the sequence in the alignment\
 **end** – end of the sequence in the alignment

**setColoring(coloring)** – set coloring, one of the following:

Value Description:\
 **disable** - Disable alignment score coloration\
 **fbd** – DNA/Protein: Score residues based on their frequency in the
column\
 **diff** – DNA/Protein: Score residues based on match/mismatch to a
master/anchor row\
 **na** – DNA: Assign color based on residue (A – Red, G – Blue, C –
Yellow, T – Green)\
 **cq\_na** – DNA: Score residues based on how well a particular residue
agrees with the others in a column\
 **cq\_aa** – Protein: Score residues based on how well a particular
residue agrees with the others in a column.\
 **rasmol** – Protein: Used by the application RasMol to group amino
acids with similar properties\
 **shapely** – Protein: Used by the application RasMol to group amino
acids with similar shapes using a standard color table\
 **blosum45** – Protein: Matrix made by matblas from blosum45.iij BLOSUM
Clustered Scoring Matrix in 1/3 Bit Units\
 **blosum62** – Protein: Matrix made by matblas from blosum62.iij BLOSUM
Clustered Scoring Matrix in 1/2 Bit Units\
 **blosum80** – Protein: Matrix made by matblas from blosum80.iij BLOSUM
Clustered Scoring Matrix in 1/2 Bit Units\
 **hydropathy** – Protein: Side chain hydropathy, corrected for
solvation\
 **membrane** – Protein: Membrane-buried preference parameters\
 **signal** – Protein: Signal sequence helical potential\
 **size** – Protein: Amino acid size

**getColoring()** – returns current coloring.

Embedding Demos
---------------

[Static Embedding Demo](/projects/msaviewer/demo_static.html)

[Dynamic Embedding Demo](/projects/msaviewer/demo_dynamic.html)

[Interaction with Sequence Viewer
Demo](/projects/msaviewer/demo_sv.html)

[Event Handling Demo](/projects/msaviewer/demo_events.html)

[Coloring Demo](/projects/msaviewer/demo_coloring.html)

[Alignment Coordinate Transformation
Demo](/projects/msaviewer/demo_mapping.html)



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

