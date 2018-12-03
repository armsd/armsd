![img](./aRMSD_logo.png)

`aRMSD` is an open toolbox for the structural comparison of two
constitutionally identical molecules.  The data are read from common
file formats (e.g., `*.xyz`, `*.pdb`, etc.) by default, or by
assistance of `openbabel`.<sup><a id="fnr.1" class="footref" href="#fn.1">1</a></sup> The results may be accessed
interactively as 3D rendering with `vtk`<sup><a id="fnr.2" class="footref" href="#fn.2">2</a></sup> and exported.  The
development started with Arne Wagner during his PhD
thesis in the Himmel group (University of Heidelberg) and
made available on <https://github.com/armsd/aRMSD>.

Contrasting to said original branch, *this* fork develops `aRMSD`
under Linux (Debian 10 / Buster, currently testing / Sid), since it
was used side-by-side with other programs already deployed
successfully in Linux.  Changes made within this fork, however,
should work equally in other operating systems.


# What may aRMSD do for you &#x2013; an appetizer

As shown in the figure below, `aRMSD` may be used to align the
models (a) and reorder the atom order by the Hungarian
algorithm (b). Subsequently, the superposition is optimized by
minimization of the RMSD according to the Kabsch algorithm.

![img](./aRMSD-aspirinateSteps.png "Subsequent stages comparing two models of the aspirinate anion with `aRMSD`: a) user-assisted alignment, b) re-ordering of atoms by the Hungarian algorithm, c) interactive difference rendering, d) interactive refined superposition of the models.")

In a newly designed representation (c), the differences between the
two models may be accessed visually: atoms drawn with larger
diameter indicate a larger *relative* contribution to the final RMSD
determined for the complete model.  The color scaling, corresponding
to the scale at the side, corresponds to the *absolute* difference
&#x2013; in Angstroms &#x2013; of said atom for both models in the optimized
superposition.

In addition, the program compares the corresponding bond lengths of
model and reference indicates either by green or red color encoding
if the one by the model is shorter, or lengthier than the
corresponding bond in the reference.  Not shown here, but `aRMSD`
allows the interactive readout of the differences found for selected
bond lengths, angles, and dihedral angles, too.

Equally, the program offers you an interactive 3D rendering of model
and reference with the optimized superposition (d).  This "best fit"
determined may be saved in `*.xyz` files.

On an operational system including `matplotlib`, `aRMSD` may
complement the scrutiny by computing and plotting selected
statistics.  The scaling may be altered by the user, equally in
charge to select the file format of export (`*.png`; `*.ps`, `*.eps`
`*.pdf`, `*.svg`; `*.tkiz`).

![img](./aRMSD-aspirinateStatistics.png "Statistical plots drawn by `aRMSD` about said comparison of two aspirinate model data.")

Besides the results of the Kabsch test, supplementary similarity
figures of merit like the cosine similarity or the GARD values may
be stored permanently in plain ASCII (`aRMSD_logfile.out`).

Altogether with a few test data (sub-directory `examples`), an
illustrated primer in sub-directory `docs` will guide you through
setting-up the program and detail out how to perform a basic analysis. 


# Where stands aRMSD, relatively to other programs?

`aRMSD` emerges from the pair-wise comparison of (crystallographic,
but not limited to this) models with significant user-interaction.
This offers you multiple levels to check and adjust the progress of
the analysis.  As such, a batch-wise comparison of models is not
foreseen.

Note, however, that an automate, batch-wise scrutiny of two model
data may yield wrong results.  One potential pitfall is how the
model information is handled prior to the refinement of the
structure alignment, where `aRMSD` uses the Hungarian algorithm.  To
quote Kildgaard:<sup><a id="fnr.3" class="footref" href="#fn.3">3</a></sup>

"The RMSD can be minimized by translating and rotating one set of
coordinates (the other is held fixed) because the molecules are
invariant under these operations. This will lead to the two
molecules being superimposed but can also lead to a false RMSD value
if the atoms are not ordered identically."

Independent from this problem, the conventional RMSD optimization
accounts only for *atom connectivity*, neglecting *bond order*.  As
demonstrated (and illustrated) by Temeslo<sup><a id="fnr.4" class="footref" href="#fn.4">4</a></sup>, this may
yield to results questionable from a chemists point of view.


# History & Credits

`aRMSD` was developed in Windows by Arne Wagner during his PhD
thesis in the Himmel group (University of Heidelberg, Germany).  It
is described briefly in his PhD thesis submitted in
2015.<sup><a id="fnr.5" class="footref" href="#fn.5">5</a></sup> The program was presented in further detail in

Wagner, A.; Himmel, H.-J. aRMSD: A Comprehensive Tool for Structural
Analysis.  *J. Chem. Inf. Model.*, 2017, *57*, 428&#x2013;438 (doi:
10.1021/acs.jcim.6b00516)

and originally deposit as open source code with the permissible MIT
license to the public under

<https://github.com/armsd/aRMSD>

As by November 2018, his last public github-commit regarding aRMSD
was on April 5, 2017.  My subsequent work on `aRMSD` is based on this release.


# Footnotes

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Open Babel, <http://openbabel.org/wiki/Main_Page>.  For
further details, see by O'Boyle, N. M.; Banck, M.; James, C. A.;
Morley, C.; Vandermeersch, T.; Hutchison, G. R.  Open Babel: An open
chemical toolbox. *J. Cheminf.* 2011, 3:33 (doi: 10.1186/1758-2946-3-33).

<sup><a id="fn.2" href="#fnr.2">2</a></sup> <http://www.vtk.org>

<sup><a id="fn.3" href="#fnr.3">3</a></sup> Kildgaard, J. V.; Mikkelsen, K. V.; Bilde, M.; Elm,
J. Hydration of Atmospheric Molecular Clusters: A New Method for
Systematic Configurational Sampling. *J. Phys. Chem. A* 2018, 122,
5026&#x2013;5036 (doi: 10.1021/acs.jpca.8b02758).

<sup><a id="fn.4" href="#fnr.4">4</a></sup> Temeslo, B.; Mabey, J. M.; Kubota, T.; Appiah-Padi, N.;
Shields, G. C. ArbAlign: A Tool for Optimal Alignment of Arbitrarily
Ordered Isomers Using the Kuhn-Munkres
Algorithm. *J. Chem. Inf. Model.* 2017, 57, 1045&#x2013;1054 (doi:
10.1021/acs.jcim.6b00546).

<sup><a id="fn.5" href="#fnr.5">5</a></sup> Wagner, A.  Synthese und Koordinationschemie
guanidinatstabilisierter Diboranverbindungen.  (Synthesis and
Coordination Chemistry of Guanidinate-Stabilised Diboranes) PhD thesis
(2015), University of Heidelberg (Germany).  Written in German
including an English summary.  The pdf of this document may be found
at the doi 10.11588/heidok.00019018.
