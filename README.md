# Graph Code Viewer — sample dataset

Interactive viewer for the graph-code datasets: CSS codes on bipartite graphs and general
stabilizer codes on connected graphs, each code given by a graph, its stabilizer generators
and its logical operators.

**▶ [Open the viewer](https://mmehrani.github.io/graph-code-viewer/)**

> **This is a trial version, not the complete visualisation of all graph codes.**
> It carries at most **two sample codes per (n, k, d, degeneracy) category** — 41 codes in
> 21 categories. The complete dataset (millions of codes) will be released with the paper.

## What is here

| family | n | categories | sample codes |
|---|---|---|---|
| CSS (bipartite graphs) | 7, 8, 9, 10, 11 | 13 | 25 |
| general stabilizer | 5, 6, 7, 8 | 8 | 16 |

A *category* is a combination of (n, k, d, degeneracy): number of qubits, logical qubits,
distance, and whether the code is degenerate. Where a category spans more than one
local-Clifford (LC) equivalence class of graph states, the two samples are taken from
different classes, so the *Next / Previous LC class* buttons still do something.

Left out entirely because of their size: general stabilizer n = 9 (2.5 GB), CSS n = 12
(30 MB) and CSS n = 13 (1.7 GB).

[`demo_manifest.json`](demo_manifest.json) lists every sample with its graph6 string, LC class
and the line it occupies in the corresponding file of the full dataset.

## Using it

Open the link above. The sample dataset loads by itself and the page starts on the [[5, 1, 3]]
code — the 5-cycle graph — so there is nothing to set up. Then pick the code family, set n and
any of k, d, degeneracy and the check-matrix row/column weight limits (blank = any), and press
**Search** — or paste a graph6 string to look a specific graph up.

A section at the top explains what a graph state is, what the CWS form of a stabilizer code is,
and why each card is a logical basis of the codespace; the references are at the bottom of the page.

Each result card shows the graph with labelled vertices, one copy per logical operator with
the qubits it acts on filled in, the stabilizer generators as a table and as Pauli strings,
the logical X and Z operators, the row/column weights, the number of correctable pairs and the
LC class of the graph state. Vertices can be dragged, the layout switched between
spring / circle / bipartite, and the drawing downloaded as SVG.

The viewer reads the `graphsNCSS*.gz` / `graphsNLDPC*.gz` files served next to the page and
streams them in the browser; nothing is ever uploaded.

### A note on the counts

The hints above the results (*"Full dataset: N codes match …"*, *"Graph states: N LC
classes"*) are computed from lookout tables for the **complete** dataset. They are correct
statements about the full data, but the files served here hold only the samples, so a search
normally returns far fewer results than the hint announces. Line numbers on the result cards
likewise refer to these demo files, not to the full dataset — see `demo_manifest.json` for the
original line numbers.

## Browser support

Needs streaming gzip (`DecompressionStream`): Chrome/Edge 80+, Firefox 113+, Safari 16.4+.

## Rebuilding

The site is generated from the research repository by `viewer/make_demo_site.py`, which samples
the `*_lc_class_included.gz` dataset files and injects the trial banner into the viewer.
