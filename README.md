# Corsair Components ESOP Plan Knowledge Graph

[![DOI](https://zenodo.org/badge/1385890635.svg)](https://doi.org/10.5281/zenodo.22945451)

A checked knowledge graph of a real, public Employee Stock Ownership Plan. It shows how a legal plan document can become a graph where every rule, term and legal citation is linked and traceable.

Built and maintained by **Craig Hodges**, founder of [GoalC.ai](https://www.goalc.ai/about.html) (ALC, Inc.).

## The source document

This graph is built from the **Corsair Components, Inc. Employee Stock Ownership Plan**, amended and restated as of January 1, 2011. It was filed publicly with the SEC as Exhibit 10.20:

https://www.sec.gov/Archives/edgar/data/1486183/000119312512186418/d52593dex1020.htm

The company is no longer an ESOP. The plan is used here only as a public example.

## What is in it

- **114 nodes, 1,083 facts.**
- **All 22 plan sections**, with summaries and the rules inside them: vesting, allocation, distribution, put options, diversification, top-heavy rules and more.
- **18 defined terms.** The terms added in version 1.1 are quoted word for word from the plan and link back to the SEC filing.
- **29 tax code sections and 5 ERISA sections**, each linked from the plan sections that cite them.
- **A cross-reference index** that maps cells in an ESOP waterfall spreadsheet to the plan provision and tax code section behind each number.

## Files

| File | What it is |
|---|---|
| `graph.jsonld` | The graph, in JSON-LD. |
| `shapes.ttl` | The rules the graph must follow, written in SHACL (the W3C standard for checking graphs). |
| `validation/results.json` | Machine-readable results of the latest check. |
| `validation/conformance-report.docx` | Plain-language summary of the latest check. |

## Proof it was checked

Version 1.1 passes its rules with **zero violations**.

The rules were written by hand to say what a correct ESOP graph must look like, not just what this one contains. They require things like:

- Every section, term and legal citation has a name, version, review date and a confidence score between 0 and 1.
- Every defined term has a real definition.
- Every link from a plan section to a term, tax code section or ERISA section points to a node that exists and is the right kind.

The first check of version 1.0 found 149 problems. Links were stored as plain text, and 16 references pointed to nodes that did not exist. Version 1.1 fixed all of them, using the plan's own wording.

### Run the check yourself

```bash
pip install pyshacl
pyshacl -s shapes.ttl -sf turtle -df json-ld graph.jsonld
```

A result of `Conforms: True` means the graph passed.

## Important note

This graph is for learning and demonstration. It is not legal or tax advice. Laws and dollar limits change. Check the current rules with a qualified advisor.

## Explore it online

- Browse it: https://www.goalc.ai/kg/corsair-esop/explorer.html
- All public graphs: https://www.goalc.ai/kg/

## License

The graph structure, summaries and rules are [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). You may share and adapt them for noncommercial use, with credit to Craig Hodges / GoalC.ai. Quoted plan text comes from a public SEC filing. For commercial use, contact craighodges@goalc.ai.

## Cite it

Archived on Zenodo with a permanent DOI:

- All versions: [10.5281/zenodo.22945451](https://doi.org/10.5281/zenodo.22945451)
- This version (v1.1.0): [10.5281/zenodo.22945452](https://doi.org/10.5281/zenodo.22945452)

> Hodges, C. (2026). *Corsair Components ESOP Plan Knowledge Graph* (v1.1.0). Zenodo. https://doi.org/10.5281/zenodo.22945451

See also `CITATION.cff`, or use the "Cite this repository" button on GitHub.
