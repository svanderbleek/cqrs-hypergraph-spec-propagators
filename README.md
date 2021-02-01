# cqrs-hypergraph-spec-propagators

title is a joke, research dumping ground for formal models of api dependencies

## Research

* Dependency graphs with applications to verification http://people.cs.aau.dk/~srba/files/ELMS:STTT:20.pdf

## Tools

* a verification tool for weighted kripke graphs https://github.com/jonasfj/WKTool

> WKTool is a verification tool for weighted Kripke structures. It permits the specification of systems by the means of a CCS-like language. Properties are expressed using a weighted dialect of computation tree logic.

The verification engine relies on fixed point computation on dependency graphs (See: Xinxin Liu, Scott A. Smolka: Simple Linear-Time Algorithms for Minimal Fixed Points). Queries may also be encoded in symbolic dependency graphs, which can be more efficient for large bounds. Moreover, the engine supports both global and on-the-fly exploration of the state-space.

## Industry

* Conventional Commits https://www.conventionalcommits.org/en/v1.0.0/
