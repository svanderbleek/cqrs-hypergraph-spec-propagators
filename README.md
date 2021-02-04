# cqrs-hypergraph-spec-propagators

title is a joke, research dumping ground for formal models of api dependencies

there's too much existing research to finish a literature review given time limit so just going to build something

## Motivation

* Versioning of Events in Event Sourced Systems https://www.infoq.com/news/2017/07/versioning-event-sourcing/

> A challenge with event sourced systems is that events put in the event store years ago must be readable today, even though the software has gone through numerous changes, Greg Young stated in his presentation at this year’s DDD eXchange conference. There are downstream consumers like projections and other systems that must be able to handle old as well as new versions of events.

* Changelog spec
  * demo https://opticdev.github.io/changelog-spec-demo/
  * Building a Better API Specification https://useoptic.com/blog/chanelog-specs-part1

> What is a specification?

> * Simple for humans to work with and provide a great developer experience.
> * Faithfully encode the interface of the API they describe.
> * Representative of the domain with rich abstractions that are useful for the task at hand (design, code generation, doc gen).
> * Stable. Breaking changes in complex specification are expensive for users and toolmakers.
> * Easy for tooling built on the spec to query the data they need. The interface should be stable for many years and the domain logic should not have to be replicated in tooling itself.

> We need models optimized for:

> * Human Readability: so programmers can easily read and understand the API being spec'd.
> * Human Writability: so programmers can quickly write and modify the spec with productive abstractions.
> * Machine Readability: so tools can query the information in the spec relevant to them.
  
> Many important questions can be answered with nothing but the facts ie "Which fields are required?"

> Some questions may compare the state of the spec to some external data ie "Does this JSON match the shape with ID 'root'?"

> And another class of questions are about how the domain has changed over time, ie "What's changed since offset X?"

> Some example projections might be:

> * A list of endpoints — That is all you get. There is nothing you do not need.
> * A list of schemas / types represented as a list of rules (great for building a test suite), with all their references flattened, or as a JSON schema.
> * Your API represented in OpenAPI — A traditional spec format is just another projection of the core data model. Even some of Optic’s more advanced features, such as support for Generics, can be projected onto OpenAPI.
> * the changes made since the last version of the API.
> * projections optimized for generating code

* git for apis https://useoptic.com/blog/git-for-apis

## Definitions

* CQS https://en.wikipedia.org/wiki/Command%E2%80%93query_separation

> Command–query separation (CQS) is a principle of imperative computer programming. It was devised by Bertrand Meyer as part of his pioneering work on the Eiffel programming language.

> It states that every method should either be a command that performs an action, or a query that returns data to the caller, but not both. In other words, Asking a question should not change the answer.[1] More formally, methods should return a value only if they are referentially transparent and hence possess no side effects.

* CQRS https://martinfowler.com/bliki/CQRS.html#:~:text=CQRS%20stands%20for%20Command%20Query,you%20use%20to%20read%20information.

> CQRS stands for Command Query Responsibility Segregation. It's a pattern that I first heard described by Greg Young. At its heart is the notion that you can use a different model to update information than the model you use to read information. For some situations, this separation can be valuable, but beware that for most systems CQRS adds risky complexity.

* CQRS MSFT https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs

* Distributed version control https://en.wikipedia.org/wiki/Distributed_version_control

> In software development, distributed version control (also known as distributed revision control) is a form of version control in which the complete codebase, including its full history, is mirrored on every developer's computer.[1] Compared to centralized version control, this enables automatic management branching and merging, speeds up most operations (except pushing and pulling), improves the ability to work offline, and does not rely on a single location for backups.[1][2][3][4] Git, the world's most popular version control system,[5] is a distributed version control system.

* dependence analysis https://en.m.wikipedia.org/wiki/Dependence_analysis

* projectional editing https://martinfowler.com/bliki/ProjectionalEditing.html

* most general unifier http://www.mathcs.duq.edu/simon/Fall04/notes-7-4/node6.html

> There is a simple algorithm for finding the most general unifier of a set of expressions. First, we need to define the disagreement set of a set of expressions. This is found by (textually) finding the first symbol starting from the left that is not the same in every expression and extracting the subexpressions that begin with that symbol at that position in each expression of the set. The resulting set of subexpressions is the disagreement set.

> If one is willing to use a dag (directed acyclic graph) representation for terms, then this exponential growth rate does not occur. Paterson and Wegman [1978] have given an efficient linear-time unification algorithm based on representing terms as dags.

* propagators https://groups.csail.mit.edu/mac/users/gjs/propagators/
  * https://github.com/ekmett/propagators

* bounded join semilattice https://en.m.wikipedia.org/wiki/Semilattice

* property graph https://en.wikipedia.org/wiki/Graph_database#Labeled-property_graph

* linked open data https://en.wikipedia.org/wiki/Linked_data#Linked_open_data

* notation3 https://en.wikipedia.org/wiki/Notation3

* software product lines https://en.wikipedia.org/wiki/Software_product_line#:~:text=Software%20product%20lines%20(SPLs)%2C,a%20common%20means%20of%20production.

* feature oriented domain analysis https://en.wikipedia.org/wiki/Feature-oriented_domain_analysis

* https://en.m.wikipedia.org/wiki/Tracing_(software)

* abstract interpretation https://en.m.wikipedia.org/wiki/Abstract_interpretation

* symbolic execution https://en.m.wikipedia.org/wiki/Symbolic_execution

* american fuzzy lop https://en.wikipedia.org/wiki/American_fuzzy_lop_(fuzzer)

* dynamic program analysis https://en.wikipedia.org/wiki/Dynamic_program_analysis

* galois connection https://en.wikipedia.org/wiki/Galois_connection

* shape analysis https://en.m.wikipedia.org/wiki/Shape_analysis_(program_analysis)

## Research

* Hermes: an efficient algorithm for building Galois sub-hierarchies

* Computing interfaces in Java https://www.researchgate.net/profile/Marianne_Huchard/publication/2404076_Computing_Interfaces_in_Java/links/0f3175319d648cfaed000000/Computing-Interfaces-in-Java.pdf

* Incremental concept formation algorithms based on Galois (concept) lattices

* SEMANTICS-BASED CHANGE-MERGING OF ABSTRACT DATA TYPES 

* Building and Maintaining Analysis-Level Class Hierarchies Using Galois Lattices

>  Class hierarchies start taking shape at the analysis level, where classes that share application-significant data and application-meaningful external behavior are grouped under more general classes. At the design level, such hierarchies are augmented with implementation classes, and possibly reorganized to take into account implementation factors such as performance or code reuse [22]. Getting the analysis-level hierarchy "right" is very important for the understandability and traceability of the models and the reusability of the resulting code [22]. In this paper, we propose a formal method that organizes a set of class interfaces into a lattice structure called Galois Lattice [10]. Such a lattice has several advantages including: 1) embodying protocol conformance, 2) supporting an incremental updating algorithm [9]), with applications for class hierarchy maintenance.

* Identifying modules via concept analysis

* FastRCA-Seq: An efficient approach for extracting hierarchies of multilevel closed partially-ordered patterns

* Constructive consistency checking for partial specication
in Z 

> Partial specifcation is a method of specifying complex systems in which the system is described by a collection of specifications, each approaching the system from a diffrent viewpoint. The specification notation Z is often advocated as a suitable language for this style of specifi- cation. For collections of partial specications to be meaningful, they need to be consistent, i.e. they should not impose contradictory requirements. This paper addresses how the consistency between partial specifications in Z can be checked, by constructing unifications, i.e. least common refinements, of viewpoint specidfications.

* Identification multi-level frequent usage patterns from apis

> This article presents an approach to identify multi-level frequent usage patterns (IML-FUP) to help developers understand API usage and facilitate the development tasks when they use new APIs. An identified pattern represents a set of API methods that are frequently called together across interfering usage scenarios

* Identifying software components from object-oriented APIs based on dynamic analysis

* Runtime monitoring in continuous deployment by differencing execution behavior model

* Towards assisting developers in API usage by automated recovery of complex temporal patterns

* Correctness enhancement: a pervasive software engineering paradigm

> In this paper, we discuss mathematics of correctness enhancement, i.e., the process of making a program more correct than it is with respect to a specification;

* Projecting programs on specifications: Definition and implications

> Given a specification R, it is common for a candidate program P to be doing more than R requires; this is not necessarily bad, and is often unavoidable, due to programming language constraints or to otherwise sensible design decisions. In this paper, we introduce a relational operator that captures, for a given specification R and candidate program P, the functionality delivered by P that is relevant to R. This operator, which we call the projection of P over R (for reasons we explain), has a number of interesting properties, which we explore in this paper.

* API Misuse Detection An Immune System inspired Approach

> We built APIMMUNE, a novel API misuse detector. We collect normal usages of a given APIs from the set of client programs using the APIs, especially after some API usages were fixed in those programs. The normal API usages are considered as normal body cells. We transform them into normal-usage signatures. Then, artificial detectors are randomly generated by generating artificial deviations from these usages with the objective of being different from the normal usage signatures. The generated detectors have the ability to detect risky uses of APIs exactly as the immune system detects foreign cells of the organism. 

* A fast algorithm for building lattices

* The concept of dynamic analysis

* Service-oriented architecture

> This paper attempts a definition of service derived by unifying its usage in practice. In doing so it identifies participant's perspective as separate from actual different usages. Using this as an aid, the paper analyses the criteria applied in the use of service and considers how these can be aligned to derive commonality underlying the usage. Also included is a brief outline of the way in which a service-oriented architecture following such a model would affect the practice and process of developing large-scale, distributed software systems.

* Building and maintaining analysis-level class hierarchies using galois lattices

> In this paper, we propose a formal method that organizes a set of class interfaces into a lattice structure called Galois Lattice [10]. Such a lattice has several advantages including: 1) embodying protocol conformance, 2) supporting an incremental updating algorithm [9]), with applications for class hierarchy maintenance.

* On the lattice of specifications: Applications to a specification methodology

> In this paper we investigate the lattice properties of the natural ordering between specifications, which expresses that a specification expresses a strongerrequirement than another specification. The lattice-like structure that we uncover is used as a basis for a specification methodology.

* Resource and Dependency based Test Case Generation for RESTful Web Services https://github.com/EMResearch/EvoMaster/blob/master/docs/publications/2021_emse.pdf

> In this paper, we propose an enhanced search-based method for automated system test generation for RESTful web services, by exploiting domain knowledge on the handling of HTTP resources. The proposed techniques use domain knowledge specific to RESTful web services and a set of effective templates to structure test actions (i.e., ordered sequences of HTTP calls) within an individual in the evolutionary search. The action templates are developed based on the semantics of HTTP methods and are used to manipulate the web services’ resources. In addition, we propose five novel sampling strategies with four sampling methods (i.e., resource-based sampling) for the test cases that can use one or more of these templates. The strategies are further supported with a set of new, specialized mutation operators (i.e., resource-based mutation) in the evolutionary search that take into account the use of these resources in the generated test cases. Moreover, we propose a novel dependency handling to detect possible dependencies among the resources in the tested applications. The resource-based sampling and mutations are then enhanced by exploiting the information of these detected dependencies. 

* OAS DB: A Repository of Specifications to Support OpenAPI Research

> There do exist directories of APIs (e.g., RapidAPI2)and even collections of OpenAPI specifications (e.g., APIs Guru3 ). However, these existing solutions are not a good fit for researchers for two important reasons. The first one is the lack of annotations in the OpenAPI samples, making it challenging for a researcher to check the performance of a tool tested against these existing solutions. Without annotated samples, it becomes labor intensive to produce metrics because one has to manually analyze every specification touched by the tool under assessment (e.g., to confirm true positives). The second reason is the fact that the focus of these repositories is simply on creating OpenAPI specifications for existing web services, without a concentrated effort (such as in the case of OAS DB) in adding new samples that actually increase the diversity of scenarios covered (both in terms of anti-patterns contained in the repository and in terms of domains covered by its samples).

* RESTest: Black-Box Constraint-Based Testing of RESTful Web APIs

> In this paper, we present RESTest, a framework for automated black-box testing of RESTful APIs. Among its key features, RESTest supports the specification and automated analysis of interparameter dependencies, enabling the use of constraint solvers for the automated generation of valid test cases.

* Checking Security Properties of Cloud Service REST APIs

> We define a REST API as a finite set of requests. Each request r is a tuple of the form ha, t, p, bi where

> • a is an authentication token,
> • t is the request type,
> • p is a resource path, and
> • b is the request body.

> A request type t is any of the following five REST-allowed values: PUT (create or update), POST (create or update), GET (read, list or query), DELETE (delete), PATCH (update). The resource path p is a string identifying a cloud resource and its parent hierarchy. Typically, p is a (non-empty) sequence matching the regular expression (/hresourceTypei/hresourceNamei/)+ where resourceType denotes the type of a cloud resource and resourceName is the specific name of the resource of that type. 

> Active property checking versus passive monitoring. As discussed earlier, the checkers we define extend the search space explored by the main driver with additional test cases aimed at triggering and detecting specific rule violations. In contrast, passive runtime monitoring of these rules in conjunction with the main driver, i.e., without executing those new tests, would likely be unable to detect rule violations.

* Capturing and Enhancing In Situ System Observability for Failure Detection

* Combining model checking and data-flow analysis

* JaVerT: JavaScript verification toolchain

* JaVerT 2.0: Compositional symbolic execution for JavaScript

* IDEal: efficient and precise alias-aware dataflow analysis.

* From Start-ups to Scale-ups: Opportunities and Open Problems for Static and Dynamic Program Analysis

* Go with the flow: compositional abstractions for concurrent data structures

* Armada: low-effort verification of high-performance concurrent programs

* Deploying Search Based Software Engineering with Sapienz at Facebook

* Machine learning testing: Survey, landscapes and horizons

* Continuous reasoning: Scaling the impact of formal methods

* An Interface Theory Based Approach to Verification of Web Services 

* Towards Formal Interfaces for Web Services with Transactions

> Let M be a finite set of Web methods, O be a finite set of outcomes, and dom(f)denote the domain of the function f.

* Interface Theory based Formalization and Verification of Orchestration in BPEL4WS

* Gillian: Compositional Symbolic Execution for All

* CrySL: An Extensible Approach to Validating the Correct Usage of Cryptographic APIs

* Continuous Reasoning for Real-World Program Analysis Tools

* An Interface Theory for Program Verification https://link.springer.com/chapter/10.1007/978-3-030-61362-4_9

> We start with the interface   𝐼𝑃  of the program itself, which represents all traces of program executions. To prove correctness, we try to construct a more abstract interface   𝐼𝐶  of the program (overapproximation) that satisfies the specification. This interface, if found, represents more traces than   𝐼𝑃  that are all correct (satisfying the specification). Ultimately, we want a compact representation of the program behavior as a correctness interface   𝐼𝐶  in terms of inductive invariants. We can then extract a correctness witness, in standard exchange format, out of such a correctness interface. Symmetrically, to prove violation, we try to construct a more concrete interface   𝐼𝑉  of the program (underapproximation) that violates the specification. This interface, if found, represents fewer traces than   𝐼𝑃  that are all feasible (can be executed). Ultimately, we want a compact representation of the program behavior as a violation interface   𝐼𝑉  in terms of a violating program trace. We can then extract a violation witness, in standard exchange format, out of such a violation interface. This viewpoint exposes the duality of these two tasks — proving correctness and violation. It enables the decomposition of the verification process, and its tools, into (at least!) three components: interface synthesizers, refinement checkers, and specification checkers

* An Under-Approximate Relational Logic Heralding Logics of Insecurity, Incorrect Implementation & More

* Incorrectness Logic

* Compositional Shape Analysis by means of Bi-Abduction

> This paper describes a compositional shape analysis, where each procedure is analyzed independently of its callers. The analysis uses an abstract domain based on a restricted fragment of separation logic, and assigns a collection of Hoare triples to each procedure; the triples provide an over-approximation of data structure usage. Compositionality brings its usual benefits – increased potential to scale, ability to deal with unknown calling contexts, graceful way to deal with imprecision – to shape analysis, for the first time. The analysis rests on a generalized form of abduction (inference of explanatory hypotheses) which we call bi-abduction. Biabduction displays abduction as a kind of inverse to the frame problem: it jointly infers anti-frames (missing portions of state) and frames (portions of state not touched by an operation), and is the basis of a new interprocedural analysis algorithm

* V2: Fast Detection of Configuration Drift in Python

* The Dynamics of Software Composition Analysis

> Software Composition Analysis (SCA). SCA products are concerned with three tasks: discovering dependencies, checking the reachability of vulnerable code for false positive elimination, and automated remediation. The latter two tasks rely on call graphs of application and library code to check whether vulnerabilityspecific sinks identified in libraries are used by applications. However, statically-constructed call graphs introduce both false positives and false negatives on real-world projects. In this paper, we develop a novel, modular means of combining call graphs derived from both static and dynamic analysis to improve the performance of false positive elimination

* Analysing Socio-technical Congruence in the Package Dependency Network of Cargo

*  Efficient static checking of library updates https://asankhaya.github.io/pdf/Efficient-Static-Checking-of-Library-Updates.pdf

> To address this problem, we present a static analysis for automatically and efficiently checking if a library upgrade introduces an API incompatibility. Our analysis does not rely on reported version information from library developers, and instead computes the actual differences between methods in libraries across different versions. The analysis is scalable, enabling real-time diff queries involving arbitrary pairs of library versions.

* A4: Automatically Assisting Android API Migrations Using Code Examples

> In this paper, we propose an approach that automatically learns API migration patterns from code examples and applies these patterns to the source code of Android apps for API migration. 

* Exploring the Use of Automated API Migrating Techniques in Practice: An Experience Report on Android

* Declaration patterns in dependency management

> Several tools are available that assist with automating the process of updating declarations as needed. Greenkeeper16, Dependabot17, and Dependencies.io18 are some of the services that sit within a continuous integration service or as a git repository plugin, sending pull requests to update declarations whenever dependency updates occur. This allows developers to test the branch containing the dependency update (some services build the project and run its regression tests automatically to further automate the process), and merge it if there are no issues. Automating this process gives instant feedback to developers when dependency updates have occurred, meaning that developers can at least know that the dependency update exists and decide if they want to update immediately or delay the update. Another tool, Snyk19, works in a similar way to alert developers of security vulnerabilities in their dependencies. For both types of tools, the emphasis is on providing a quick transfer of information, solving the issue that researchers have pointed out about developers often being unaware of updates or vulnerabilities.

> There are a number of tools that can detect breaking API changes, including clirr20 (widely used in research but not updated since 2005) and Revapi21 for Java, or NDepend22 for .NET. In Section 3.3.3, PDE API Tools23 was also discussed as a tool used by the Eclipse community which does a similar job. These are helpful for detecting API changes, and pinpoint where developers must look closely at the dependency updates, and in some cases can be plugged into tools such as Maven, Visual Studio or cloud-based platform tools. This integration with the automated build cycle is desirable - making the build process as automated as possible [Humble and Farley, 2010], and is considered best practice within DevOps. Jezek and Dietrich benchmarked nine API compatibility tools against a suite of API breaking changes, finding that there are now some highly usable and accurate tools available [Jezek and Dietrich, 2017]. For all API compatibility tools, it should be noted that they only focus on API changes, and ignore that semantic changes within projects can also be breaking, so they only cover one aspect of compatibility.

> Foo et al. report on an API incompatibility checker that uses static analysis [Foo et al., 2018]. A statically constructed callgraph is used to detect deep changes that can effect compatibility. The tool works for the Maven, PyPi, and RubyGems ecosystems, and the authors report that based on the experiments with the tools, 26% of library versions are in violation of semantic versioning. The authors caution that this analysis suffers from the imprecision of the static analysis being used (VTA) though, with a large amount of false positives being associated with this method.

* Will Dependency Conflicts Affect My Program’s Semantics? https://arxiv.org/pdf/2006.07633.pdf

* Prazi: From Package-based to Call-based Dependency Networks https://arxiv.org/pdf/2101.09563.pdf
  * https://github.com/praezi/rust

> To better model dependencies between packages, we devise Prazi ¨ , an approach combining manifests and call graphs of packages. Prazi constructs a fine-grained dependency network at the more fine-grained function-level, instead of at the manifest-level.

* Dependency Versioning in the Wild https://researchspace.auckland.ac.nz/bitstream/handle/2292/49003/2019_MSR_versioning.pdf?sequence=2

> When declaring dependencies, developers face various choices, such as whether or not to declare a fixed version or a range of versions. The former results in runtime behaviour that is easier to predict, whilst the latter enables flexibility in resolution that can, for example, prevent different versions of the same package being included and facilitates the automated deployment of bug fixes.

*  Differential regression testing for REST APIs https://patricegodefroid.github.io/public_psfiles/issta2020.pdf

> For generating inputs (sequences of HTTP requests) to services, we use RESTler, a stateful fuzzer for REST APIs. Comparing the outputs (HTTP responses) of a cloud service involves several challenges, like abstracting over minor differences, handling out-of-order requests, and non-determinism

> In order to test a service, it is necessary to exercise it with a client. In what follows, the pair (ci ,sj) will denote testing the service sj with a client ci matching (or automatically generated from) specification version i. Figure 2 shows the three possible testing configurations between the client/service versions n and n + 1 of a REST API, which are each denoted by an edge in Figure 2: 

> • (cn,sn) corresponds to the vertical edge where inputs from old clients are sent to an old service version,
> • (cn,sn+1) (the diagonal edge) is the state when the service is already updated, but the new specification not yet published, and
> • (cn+1,sn+1) is the final configuration when both clients and service are updated.

> Static Diffing to Find Specification Regressions. Our stateful and stateless approaches to diffing network logs are built upon standard algorithms for computing edit distances and edits scripts [38]. Diffing can be applied directly to Swagger specifications in order to find some types of clear regressions, such as removing a request from an API [1]. However, static diffing of specifications has its own challenges. First, these diffs can be large: for instance, the 16 diffs files obtained by pairwise diffing all 17 Azure Network API Swagger specifications in chronologic order result in a total of 15,571 lines and 465,624 bytes. Second, most differences are harmless: adding new files, reorganizing API requests, adding or modifying examples, etc. Third, even when modifying specific parameters in a new specification version, the old parameters are often still handled correctly by the new service for backwards-compatibility reasons, and therefore are not regressions; the only way to eliminate such false alarms is by dynamically testing the new service against (client code generated from) the old specification. In contrast, specification regressions can be found with stateless diffing and the diagonalonly strategy (16 diffs) by inspecting only 302 lines (see Table 4), i.e., two orders of magnitude less data compared to 15,571 lines with static diffing. Overall, static specification diffing is complementary to the dynamic testing-based approach developed in this work.

* RESTler: Stateful REST API Fuzzing

* Specification of Generic APIs, or: Why Algebraic May Be Better Than Pre/Post

>  Unlike pre/post-based specification, which deals with the inputs and outputs of one operation at a time, algebraic specification deals with the relationships between the different operations in an API, which is needed in the specification of generic APIs.

* An Exploratory Study on Faults in Web API Integration in a Large-Scale Payment Company http://pure.tudelft.nl/ws/files/42667586/mainwfonts.pdf

> 1) faults in API integration can be grouped into 11 general causes: invalid user input, missing user input, expired request data, invalid request data, missing request data, insuicient permissions, double processing, coniguration, missing server data, internal and third party, 2) most faults can be attributed to the invalid or missing request data, and most API consumers seem to be impacted by faults caused by invalid request data and third party integration; and 3) insuicient guidance on certain aspects of the integration and on how to recover from errors is an important challenge to developers.

* Opportunities in Software Engineering Research for Web API Consumption https://arxiv.org/pdf/1705.06586.pdf

> We outline two specific research threads in this context: (1) web API specification curation, which enables us to know the signatures of web APIs, and (2) static analysis that is capable of extracting URLs, HTTP methods etc. of web API calls. Furthermore, we present new work on how we combine (1) and (2) to provide IDE support for application developers consuming web APIs. 

* Inferring Web API Descriptions from Usage Data 

> We describe a set of techniques to infer structured descriptions of web APIs from usage examples. Using trained classifiers, we identify fixed and variable segments in paths, and tag parameters according to their types

* Trace Partitioning in Abstract Interpretation Based Static Analyzers http://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=E0354DE223C1928921984ED1DCF8D4D8?doi=10.1.1.80.3933&rep=rep1&type=pdf

> This paper proposes a systematic way of regaining some knowledge about the traces by performing the abstraction over a partition of the set of traces instead of the set itself. This systematic refinement is not only theoretical but tractable: we give automatic procedures to build pertinent partitions of the traces and show the efficiency on an implementation integrated in the Astrée static analyzer, a tool capable of dealing with industrial-size software.

* A Linked Open Data Approach for Web Service Evolution

> Web services are subject to changes during their lifetime, such as updates in data types, operations, and the overall functionality. Such changes may impact the way Web services are discovered, consumed, and recommended. We propose a Linked Open Data (LOD) approach for managing Web services new deployment and updates. We propose algorithms, based on semantic LOD similarity measures, to infer composition and substitution relationships for both newly deployed and updated services. We introduce a technique that gathers Web service interactions and users’ feedbacks to continuously update service relationships. To improve the accuracy of relationship recommendation, we propose an algorithm to learn new LOD relationships from Web service past interaction. We conduct extensive experiments on real-world Web services to evaluate our approach.

> Linked Open Data (LOD) - LOD is an initiative that aims at transforming traditional web of single hyperlink relation to a web of multidimensional268 H. Labbaci et al. semantic links [2].

> Multi-relation Network of Web Services - In previous research [9], we modeled Web service interactions using a multi-relation graph. Web services make-up the nodes of the graph, and the different invocations that occur between them such as composition, substitution, and subscription constitute its edges

> Similarity between Service Features Annotated with LOD Resources - This section proposes a model to compute the semantic similarity among two service features annotated with LOD resources

* Formalization of component substitutability https://hal.archives-ouvertes.fr/hal-02136485

> In this paper, we consider that component upgrade requires managing substitutability between the new and the old components. The substitutability check is based on dependency and context descriptions. It involves maintaining the availability of previously used services, while making sure that the effect of the new provided services do not disrupt the system and the context invariants are still preserved. We present here a formal definition and a verification algorithm for safe component substitutability.

> Component substitutability To decide whether a component Cnew can substitute a component Cold, it is necessary to compare what they provide and what they require. Indeed, the provided (or required) services of Cnew can be the same or different from those of Cold. We therefore have to study all the possibilities. Fig. 4 depicts the different possible relations between the old and the new set of provided (resp. required) services:

> • case 1: the set of provided (resp. required) services of Cnew is included in
the set of provided (resp. required) services of Cold;
> • case 2: the set of provided (resp. required) services of Cnew and Cold are
equal;
> • case 3: the set of provided (resp. required) services of Cold is included in
the set of provided (resp. required) services of Cnew;
> • case 4: the two sets are different from each other and can have some services
in common.

> We have defined the strict and the contextual substitutability and we have concentrated only on contextual one. We have presented an analysis of different substitutability cases and summarized them into three key conditions. These conditions involve checking the installability rule of the new component (verifying requirement and ensuring that provided services will not conflict with the context of the system) and checking the effect of deinstallation of the old component using the dependency graph. A prototype implementing our proposal has been developed in Ocaml. Our objective is to ensure the safety of substitutability without being restrictive by authorizing all cases of substitutability. For example, replacing a component which has a lot of unused services with another which has fewer provided services (only those which are useful) is possible. This substitutability can also depends on a system policy or property models as described in [3]. We focus on ensuring the safety of the system, i.e., verifying the requirements, the effect of the substitution and preserving context invariants, component and service properties.

* On The Evolution of Services https://d1wqtxts1xzle7.cloudfront.net/30771585/IEEE-TSE__preprint_.pdf?1362339159=&response-content-disposition=inline%3B+filename%3DOn_the_evolution_of_services.pdf&Expires=1612326971&Signature=CNsysKgy2XxqRozOmNS2vCMXCT8m~kpFRHrNmEl8W17c27OQTnPF7TkyM516vJvbvIKCjwxSYD7CyhlYjGBTEN5Hz0Z6kU8uXmA5up0dH12sXhxnIXHeaDWeDpPHvoNXu1L9EbilUjLEMiCvzDKmoffHcrM7UH5-yqBpWMb0mv9OswVk-~51yY1a31vDipVWRZO~3c8oRd-Aq0D70PtR~FaKxdHbXMhans93E8DanabRcbFTDJteQeMykyXNnqDX4d0DG-IDGwNedUI-Ey2NDDd0V6OtSkmnNJnGAfSxt8ODxheL4jFy-GW8AdlzJf9OfbqQLZmsrjXkMB17RkfaxA__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA

> Definition 4: Service Compatibility We define three cases of compatibility:

> • Forward: S <f S ⇔ ∀s ∈ Spro, ∃s ∈ S pro, s ≤ s (covariance of output).
> • Backward: S <b S ⇔ ∀s ∈ S req, ∃s ∈ Sreq, s ≤ s (contravariance of input).
> • Full: S <c S ⇔ S <f S ∧ S <b S

> These definitions are in line with both traditional type theory and with the language-producing set-based theory proposed in [16]. Given the fact that the subset Spro represents the language produced by the service, then this definition of forward compatibility is equivalent to the informal definition given in the Background section. Furthermore, armed with this definition we can reason directly on new versions S , S, S,... of the service, comparing them on a record to record basis for checking their compatibility

> Having established a type theory for all the layers of an ASD, it becomes possible to use the subtyping relation of ASD records to check for the compatibility of service versions. Reasoning about this decision is quite straightforward: by combining Definitions 4 and 6 (as extended accordingly for each layer) we can check whether both cases of compatibility are satisfied using the definition of subtyping for ASDs. The following sections discuss how this can be achieved. 1) T-Shaped Changes: We informally define the concept of T-shaped changes as the set of changes that respect service compatibility. We use three fundamental operators to describe the changes occurring to service descriptions: add for the addition of record, del for the removal of a record and mod for the modification of the record (addition/removal of attributes or properties and so on). Combinations of these fundamental operators can be further used to produce more advanced operators like the renaming of a record. By applying these operators to an ASD S and for a record s we get the respective change IEEE TRANSACTIONS ON SOFTWARE ENGINEERING This article has been accepted for publication in a future issue of this journal, but has not been fully edited. Content may change prior to final publication. 12 

> primitives: add(s, S), del(s, S) and mod(s, S). Depending on whether s is an element or a relationship, the change primitivesare expanded accordingly: add(e, S) and add(r(es, et), S) forexample signify the addition of an element e or a relationshipr(es, et) to S, respectively.The evolution of services rarely occurs in simple incrementsand usually encompasses a number of changes to the servicedescription that occur simultaneously. For this reason wedefine a change set as the fundamental degree of change to aservice description: Definition 7: A change set ΔS is a set of change primitives

> ΔS := {operator(si, S)|operator ∈ {add, del, mod}}

> that when applied to an ASD S results in a new version of
the service S, signified by S = S ◦ ΔS. Versions of services can therefore be expressed in terms ofthe change sets that are required for reconstructing a version from a baseline (original) version, following the conventions of SCM. For the purposes of this discussion we assume that the change sets between ASDs are recorded during the development of the services. If not, then the application of an algorithm like the one presented in [39] could generate them.

> 2) Behavioral Layer: The behavioral layer contains the records describing the perceived behavior of the service in terms of exchanges of messages grouped under service operations, and the conditions under which message exchanges may occur.

> A number of different techniques have been proposed for describing and reasoning on the exchange of messages, such as business protocols based on finite state machines [27], [28] or deterministic finite automata [29], formal languages like TLA+ [30], communication action schemas [31], workflows [32], automata [33], timed protocols [34] and Calculus of Communicating Systems (CCS)-like constructs [22]. A notation for the behavioral description of services (called (behavioral) contracts) has been proposed in [22], which is conceptually very similar to our approach. For this reason we rely on that work for the definition of behavioral description and show how the necessary constructs for applying it are incorporated into our model.

> In this paper we presented a theoretical framework and language-independent mechanisms to assist service developers in controlling and managing service changes in a uniform and consistent manner. For this purpose we distinguished between shallow (small-scale, localized) changes and deep (large-scale, cascading) changes and we focused on shallow changes. In particular, we provided a sound theory for service compatibility and reasoning mechanisms for delimiting the effect of changes which we keep local to and consistent with a service description. The approach proposed in this paper is in contrast to thevast majority of existing approaches in the field. Most such approaches view service compatibility as strictly enforced by a set of empirical and technology-specific rules (e.g. WSDLdependent guidelines) which indicate which changes are characterized as being compatible. This results in a very strict service evolution regime which prohibits potentially legitimate changes from being applied due to the limitations of current service technologies. We presented a formally-backed compatible service evolution framework which is based on a technology-agnostic notation for the representation of services in the form of Abstract Service Descriptions (ASDs). ASDs act as a springboard to explain the versioning mechanisms for services. Using these results, we formally defined service compatibility and developed a theory for the compatible evolution of services. As part of this approach we introduced the notion of Tshaped changes, which enforce service compatibility between interrelated service versions in two dimensions: horizontally and vertically. We also demonstrated how to reason about the compatibility of service versions using the Compatibility Checking Function (CCF) in order to decide if changes to them are T-shaped or not. 

* Dynamic Computation of Change Operations in Version Management of Business Process Models https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.673.634&rep=rep1&type=pdf

> Version management of business process models requires that changes can be resolved by applying change operations. In order to give a user maximal freedom concerning the application order of change operations, position parameters of change operations must be computed dynamically during change resolution. In such an approach, change operations with computed position parameters must be applicable on the model and dependencies and conflicts of change operations must be taken into account because otherwise invalid models can be constructed. In this paper, we study the concept of partially specified change operations where parameters are computed dynamically. We provide a formalization for partially specified change operations using graph transformation and provide a concept for their applicability. Based on this, we study potential dependencies and conflicts of change operations and show how these can be taken into account within change resolution. Using our approach, a user can resolve changes of business process models without being unnecessarily restricted to a certain order.

> One area of related work is concerned with model composition and model versioning.
Alanen and Porres [1] describe an algorithm how to compute elementary change operations. Kolovos et al. [12] describe the Epsilon merging language which can be used to specify how models should be merged. Kelter et al. [11] present a generic model 13 Fig. 9. Screenshot of our prototype in WebSphere Business Modeler differencing algorithm. Cicchetti et al. [3] propose a metamodel for the specification and detection of syntactical and semantical conflicts. In the IBM Rational Software Architect [17] or using the EMF Compare technology [7], dependencies and conflicts between versions are computed based on elementary changes. These approaches to model versioning deal with the problem of model merging but they do not make use of a model structure tree (such as our process structure tree). This enables us to compute position parameters for partially specified change operations and thereby realize iterative change resolution. In the area of software evolution, Fluri et al. [8] describe how to use abstract syntax trees and tree differencing for extracting changes and better understanding change types. Our work uses the process structure trees on the modeling level. One difference can be seen in the way change resolution is performed because on the modeling level more flexibility is needed which is incorporated by the concept of partially specified change operations. Dependencies of transformation rules have been studied in the literature: Mens et al. [19] analyze refactorings for dependencies using critical pair analysis. They first express refactorings as graph transformations and then detect dependencies using the AGG tool [23]. Graph transformations have also been used extensively for defining and parsing visual languages [21] where rules are used as parsing rules. Further, graph transformation rules have been used in various model transformation approaches (see e.g. [5, 2]), as a formal foundation as well as in transformation engines executing a 14 model transformation. In these approaches, a transformation rule is matched and applied along existing theory of graph transformation [4]. In contrast to these approaches, we study dependencies of change operations that are partially specified using J-PST dependencies and establish a relationship to TR-dependencies. In our earlier work [14], we assumed that all change operations are fully specified and in [9] we describe our general architecture. Within the process modeling community, Rinderle et al. [22] have studied disjoint and overlapping process model changes in the context of the problem of migrating process instances but have not considered dependencies between changes and different forms of change resolution.

* Capturing the Functionality of Web Services with Functional Descriptions

> While we neither have the silver bullet for universal Web service description, with this paper, we want to suggest a lightweight approach called RESTdesc. It expresses the semantics of Web services by pre- and postconditions in simple N3 rules, and integrates existing standards and conventions such as Link headers, HTTP OPTIONS, and URI templates for discovery and interaction. This approach keeps the complexity to a minimum, yet still enables service descriptions with full semantic expressiveness. A sample implementation on the topic of multimedia Web services verifies the effectiveness of our approach.

* Dependency graphs with applications to verification http://people.cs.aau.dk/~srba/files/ELMS:STTT:20.pdf

> Dependency graphs, as introduced more than 20 years ago by Liu and Smolka, are oriented graphs with hyperedges that connect nodes with sets of target nodes in order to represent causal dependencies in the graph. Numerous verification problems can be reduced into the problem of computing a minimum or maximum fixed-point assignment on dependency graphs

* A Principled Approach to Version Control https://www.andres-loeh.de/fase2007.pdf

> Version control systems are essential for managing the distributed development of large software projects. We present a formal model for reasoning about version control. In particular, we give a general definition of patch. Patches abstract over the data on which they operate, making our framework equally suited for version control of everything from highly-structured XML files to blobs of bits. We model repositories as a multiset of patches. The mathematical definitions of patches and repositories enable us to reason about complicated issues such as conflicts and conflict resolution.

* A Categorical Theory of Patches https://arxiv.org/abs/1311.3903

* A formalization of darcs patch theory using inverse semigroups

* Current Concepts in Version Control Systems https://arxiv.org/pdf/1405.3496.pdf

> Precise semantics of current version control systems are defined only loosely and the lack of formal analysis is visible especially in the area of merging algorithms. In order to get a truly reliable and dependable system with regards to merging “wild” branches exhibiting pathological behaviour, the precise semantics of various merges should be specified formally; many of the currently widely used merging methods lack detailed formal analysis and their behaviour in corner cases is only guessed. 

> There has been ongoing development in this area [20] [2], but it appears to be mostly stalled now as the recursive three-way merge and similar algorithms appear to work well enough in common cases and thus there is not much incentive to formally describe their behaviour in corner cases. However, we believe that such a formal foundation would also help development of newer changeset-oriented systems, in turn making progress with the third-party changes tracking problem.

* Real time group editors without Operational transformation https://hal.inria.fr/file/index/docid/71240/filename/RR-5580.pdf

> A real time group editor allows multiple users to edit the same text at the same time from multiple sites across Internet. The real time group editors community has developed a framework called Operational Transformation (OT) for maintaining consistency of shared data. OT differs from other optimistic replication systems by not only ensuring content consistency but also intention consistency. In this paper, we describe the WOOT (WithOut Operational Transformation) framework that ensures intention consistency without following the OT approach. However, thanks to its new viewpoint, WOOT is drastically simpler, more efficient and does not require vector clocks or central sites. The WOOT framework is particularly adapted to very large peer-to-peer networks.

* Replicated abstract data types: Building blocks for collaborative applications https://d1wqtxts1xzle7.cloudfront.net/62111772/j.jpdc.2010.12.00620200216-31699-580bsn.pdf?1581852413=&response-content-disposition=inline%3B+filename%3DReplicated_abstract_data_types_Building.pdf&Expires=1612221448&Signature=Fz7r0skIygJVTFC8yauZoCiW4nrvVLUShX5kCMAafgLaJku~U63dgA7555-4gbRREn-HbmgDh5rsR~6IaZ00qPWHxEZ~4fYLf6bWfgSCz9RfBRm7pQrqE9KsduXC6IKAk8duA2yb4InnPZevncOhlNT~rGSSRj9xLSdl6Y21uhjWxQENkYQ8DgV1-mY16IURvtJhe~uuqzI7s-UbMZlx2lnK1NNOIbtHf8bddhhfTvQA5CU8o1~ycB8v5ensJk0jvY6EJi4356YusrOAMOMfQ4cay292jdeA6b5YeD0wik6Fapq0IG9LYO9lAl2jYTsS2bd8P9EuBegyUcL93EwSoQ__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA

> For distributed applications requiring collaboration, responsive and transparent interactivity is highly desired. Though such interactivity can be achieved with optimistic replication, maintaining replica consistency is difficult. To support efficient implementations of collaborative applications, this paper extends few representative abstract data types (ADTs), such as arrays, hash tables, and growable arrays (or linked lists), into replicated abstract data types (RADTs). In RADTs, a shared ADT is replicated and modified with optimistic operations. Operation commutativity and precedence transitivity are two principles enabling RADTs to maintain consistency despite different execution orders. Especially, replicated growable arrays (RGAs) support insertion/deletion/update operations. Over previous approaches to the optimistic insertion and deletion, RGAs show significant improvement in performance, scalability, and reliability.

* Towards Versioning of Arbitrary RDF Data 

> Coherent and consistent tracking of provenance data and in particular update history information is a crucial building block for any serious information system architecture. Version Control Systems can be a part of such an architecture enabling users to query and manipulate versioning information as well as content revisions. In this paper, we introduce an RDF versioning approach as a foundation for a full featured RDF Version Control System. We argue that such a system needs support for all concepts of the RDF specification including support for RDF datasets and blank nodes. 

* Identification of Practices and Capabilities in API Management: A Systematic Literature Review

* Software Versioning with Microservices through the API Gateway Design Pattern

* first order causality http://www.lix.polytechnique.fr/Labo/Samuel.Mimram/docs/mimram_first_order_causality_long.pdf

> This work thus bridges algebra and denotational semantics in order to reveal the structure of dependencies induced by first-order quantifiers, and lays the foundations for a mechanized analysis of causality in programming languages.

* Example-driven web api specification discovery http://openaccess.uoc.edu/webapps/o2/bitstream/10609/78206/6/Ed-douibi_et_al_Example-driven_Web_API_Specification_Discovery_preprint.pdf

* Automatic generation of test cases for REST APIs: a specification-based approach https://modeling-languages.com/automatic-generation-of-test-cases-for-rest-apis/

* Towards extracting web api specifications from documentation https://annieying.ca/papers/msr18.pdf

> Web API specifications are machine-readable descriptions of APIs. These specifications, in combination with related tooling, simplify and support the consumption of APIs. However, despite the increased distribution of web APIs, specifications are rare and their creation and maintenance heavily rely on manual efforts by third parties. In this paper, we propose an automatic approach and an associated tool called D2Spec for extracting significant parts of such specifications from web API documentation pages. Given a seed online documentation page of an API, D2Spec first crawls all documentation pages on the API, and then uses a set of machinelearning techniques to extract the base URL, path templates, and HTTP methods – collectively describing the endpoints of the API.

> The web API’s base URL is essential in a web API specification: any URL of a Web API request must contain the base URL and the relative path of the corresponding endpoint. More formally, a base URL is a common prefix of all URLs for web API invocations, excluding other URLs such as documentation pages. In OpenAPI specifications, a base URL is constructed via three fields: a scheme (e.g., https), the host (e.g., api.instagram.com), and optionally a base path (e.g., /v1). In many APIs (e.g., Instagram API), the base URL is the longest common prefix of all the URLs for invoking the web API. However, for other APIs, such as Microsoft’s The DevTest Labs Client API, the longest common prefix is https://management. azure.com/subscriptions while the actual base URL is https://management.azure.com, because /subscriptions is defined to be part of the endpoint paths. Whether a base URL is indeed the longest common prefix is a design decision of the API provider. A path template defines fixed components of a URL as well as ones to be instantiated dynamically. For example, in the path template /users/{userId}/posts, the part {userId} is a path parameter that needs to be instantiated with a concrete value of a user ID before performing a request. A path parameter is typically denoted via enclosing brackets (i.e., “{}”, “[]”, “<>”, or “()”) or a prefix “:”. D2Spec focuses on one type of description associated with the path template: the HTTP method. It reflects the type of interaction to be performed on a resource exposed by a web API. While many web APIs long relied on GET and POST, now a much broader spectrum of methods is used [22]. As proposed in related work, we denote every valid combination of a path template and an HTTP method as an endpoint of the API [26].

* APIComposer: Data-driven composition of REST APIs https://modeling-languages.com/wp-content/uploads/2018/08/esocc2018.pdf

* REST API Auto Generation: A Model-Based Approach https://www.researchgate.net/profile/Samer_Zein/publication/344403957_REST_API_Auto_Generation_A_Model-Based_Approach/links/5f71dddba6fdcc0086438ed0/REST-API-Auto-Generation-A-Model-Based-Approach.pdf

* Semantic Restful Service Composition Using Task Specification

* Automated generation of client-specific backends utilizing existing microservices and architectural knowledge

* Towards better utilizing static application security testing https://www.cs.purdue.edu/homes/lintan/publications/priv-icse19.pdf

* Web application development with third-party components https://tel.archives-ouvertes.fr/tel-02101381/document

> * How to get the standard specifications of REST services?

> REST API specification. A REST API specification rigorously defines how to access the resources provided by a REST service. Several papers have focused on providing the standards of machine-readable specifications.

> — WADL: Web Application Description Language (WADL) is the de jure standard submitted by W3C in 2009 [Hadley, 2009]. WADL uses XML description to model the REST resources and their links. The XML format is machine-readable, but not human-readable. Due to its complexity, WADL doesn’t gain the interest of API
providers

> — hRESTS: HTML for RESTful Services (hRESTS) is a microformat for web developers
to make the main information machine-readable in the HTML. They add the pre-defined REST services annotations (e.g., HTTP methods, address, output) into the HTML documentation according to hRESTS format. Hence, they transform the human-readable HTML into a machine-readable one.

> — RESTdesc: RESTdesc is a semantic web service description [Verborgh et al., 2013] that based on semantic web language Resource Description Framework (RDF) [Klyne and Carroll, 2004]. It is a rule-based format that defines the preconditions, postconditions and request details of the interaction with the REST service. RESTdesc is a simple and lightweight description while still expresses the semantic of REST services.

> — WIfL: Web Interface Language (WIfL) defines a set of RDFa annotations that can be injected into the HTML [Danielsen and Jeffrey, 2013]. WIfL provides an interactive console that enables the developers to send the requests and analyze the sample responses directly in the HTML documentation. Moreover, they provide a WIfL tool that can validate the consistency of the REST APIs.

> As a summary, even though a set of specification standards has been proposed by researchers, none of them has been widely adopted by REST service providers. The industry practitioners have also proposed several descriptions, such as RAML 8,  API Blueprint 9, and OpenAPI. These API descriptions have a lot in common while OpenAPI seems to be the winner 

> * 2.2.2 Automated or semi-automated approaches . . . . . . . . . . . . . . 18

> SpyREST. Sohan et al. [Sohan et al., 2017, 2015] provide SpyREST, an approach for generating and maintaining up-to-date documentation by using an HTTP proxy server

> APIDiscoverer. Ed-douibi et al. [Ed-douibi et al., 2017] provide APIDiscoverer, an example-driven approach for generating REST API specification by using the API call (requests and responses) examples. As shown in Figure 2.5, developers need to fulfill the API calls information and send them to the REST services. It then analyzes requests and responses to generate the specification

> RESTler. Alarcon et al. [Alarcón and Wilde, 2010] provide RESTler that crawls a RESTful service and aims to generate a map that presents all the provided resources and their links. It has proposed a new description ReLL (Resource Linking Language) to describe RESTful services.

> D2Spec. Yang et al. [Yang et al., 2018; Dolby et al., 2018] provide D2Spec that extract web API specification from online documentation, which is quite similar to our work.

> * 4.3 ExtrateREST: an automated extractor for the generation of REST API specification

> ExtrateREST inputs a single index URL, gets all the documentation pages that are linked by it, selects the useful ones thanks to a machine-learning algorithm, extracts the endpoint information according to a manually-built extraction configuration, and then produces the corresponding OpenAPI specification. It is fully available as an open-source project. ExtrateREST solves two main challenges. The first one is the dispersal of the information contained in the HTML pages of a REST API documentation. It settles this challenge by classifying the HTML pages and selecting interesting ones. The second challenge is the heterogeneity of HTML layouts and vocabulary of the HTML documentations among the different service providers. It then resolves this challenge by using an extraction configuration provided by developers. The validation we performed shows that ExtrateREST produces good results for popular REST services as well as randomly selected ones. ExtrateREST returns a partial but quite complete specification for four-fifths of the popular REST services. For randomly selected REST services it is less successful mainly because the provided HTML documentation is not structured as one of the most popular REST services

> * How to adapt to the data changes of REST services?

> * 2.3.3 JSON document and JSON patch . . . . . . . . . . . . . . . . . . . . . 28

> JSON Patch. The JSON Patch RFC is an ongoing standard that specifies how to encode a patch that can be performed on a JSON document to transform it into a new one[Bryan and Nottingham, 2013]. The RFC specifies that a patch is a sequence of change operations. It then specifies the five following change operations (a sixth operation is defined to perform tests):

> — Add: this operation is performed to add a new node into the JSON document. The
new node can be added within an array or as a new property of an object.

> — Remove: this operation is performed to remove an existing node of the JSON document.

> — Replace: this operation is performed to replace an existing node by another one.

> — Move: this operation is performed to move an existing node elsewhere in the JSON document.

> — Copy: this operation is performed to copy an existing node elsewhere in the JSON document.

> The RFC specifies a standard way to encode a patch into a JSON document. More precisely a patch is an array of change operations where each change operation is encoded by a single object with properties specifying the kind of operation, the source and target nodes, and the new value if needed.

> * 2.3.4 JSON Patch Algorithms .

> JSON documents are mainly labeled unordered trees (object nodes and their properties), where some nodes are arrays, hence ordered. The theory states that when just the add, r emove and r ep l ace operations are considered, the problem of finding a minimal patch is O(n 3) for ordered trees and NP-hard for unordered trees [Zhang et al., 1992; Bille, 2005; Pawlik and Augsten, 2011; Higuchi et al., 2012]. When the move operation is also considered, the problem is NP-hard for both kind of trees [Bille, 2005]. That is why several algorithms from the document engineering research field use practical heuristics. One of the most famous is the algorithm of Chawathe et al. [Chawathe et al., 1996] that computes patches (containing move actions) on trees representing LaTeX files. Several algorithms have also been designed specifically for XML documents [Cobena et al., 2002; Al-Ekram et al., 2005]. One of them [Lindholm et al., 2006] is even capable of detecting copy operations. Several existing approaches support the creation of JSON Patches. 20 By analyzing all of them, it appears that they all take one or two of these simplifications to make the problem tractable

> — They choose not to support the move and copy operations that are yet specified in the RFC, and therefore provide non-optimal patches. As an example in the Figure 2.11, an optimal patch uses move operation to handle the property label renaming from val to va. Without such a move operation, the patch then uses a r emove property val and a add property va. Moreover, an optimal patch uses a copy operation for the property mes2 and its value copied from mes1. The Table 2.3 shows that only one existing approach does support these operations.

> — They choose not to support array node, or to support them poorly. In principle all the editing operations of the JSON RFC apply to array nodes as well as object nodes. A patch can then express changes done within an array. For instance in Figure 2.11, an optimal patch uses the move operation to put v3 to the end of the array. Moreover, it uses the copy operation for copying the existing node v1. Regarding the support of array, the Table 2.3 shows that half of the approaches do not support array at all, and consider them as a simple node (with nothing inside). The other half simply considers that an array is a stack, and therefore supports change operation that can apply to a stack (push and pop).

> * 5.2 JDR: a JSON patch algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . 66

> We evaluate the efficiency of the JavaScript implementation of our algorithm against existing JavaScript libraries that support the JSON Patch RFC. The evaluation has been done by requesting real web applications with data suggested by our industrial partner. It clearly shows that our library outperforms the other libraries. It creates a small patch quite fast, and can handle different situations (where the changes target objects’ properties or arrays). 5.4. CONCLUSION 81 As a main conclusion, we provide an efficient algorithm to create a path between two versions of a JSON document. The patch created by our approach fully complies with RFC. Even it is not optimal, it however expresses all change operations such as the move and copy ones, and the ones that target arrays

* Extracting Records from the Web Using a Signal Processing Approach https://www.researchgate.net/profile/Roberto_Velloso/publication/320882865_Extracting_Records_from_the_Web_Using_a_Signal_Processing_Approach/links/5a02ed2caca2720c3263ab7b/Extracting-Records-from-the-Web-Using-a-Signal-Processing-Approach.pdf

> We have shown here a novel approach for the problem of extracting records from semi-structured web pages based on a new insight: seeing the structure of the document as a cyclic signal

* End-to-End Versioning Support for Web Services https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.139.5552&rep=rep1&type=pdf

> Software services are, just like any other software system, subject to permanent change. We argue that these changes should generally be transparent to service consumers. However, currently consumers are often tied to a given version of a service and have no means of easily upgrading to a newer version. In this paper we propose a WSDL-driven classification of Web service change types and discuss a versioning mechanism for service-oriented systems that considers revision management on registry- and client-side. We use the concepts of service version graphs and selection strategies to provide transparent end-to-end versioning support, and show how this approach is implemented in our service-oriented computing runtime VRESCo. Furthermore, we illustrate the advantages of our approach in comparison to the current state of the art using a realistic case study

> A classification scheme for differences between Web services has been proposed by Ponnekanti et al. [13]. They specify four types of incompatibilities: structural, value, encoding, and semantics.

> In order to manage Web service evolution, service registries need to store not only the service revisions itself, but also how they relate to each other. We use the notion of service version graphs to represent these dependencies. For every service in the registry there is exactly one service version graph. These graphs are directed, with nodes representing concrete revisions of the service, and edges representing predecessor-successor relationships. The semantics of these relationships is that revision A is a predecessor of revision B, if B is the result of changes in A. All revisions in a service version graph refer to the same base service, but are on different maturity levels and represent different stages in the base service’s lifecycle.

> Selection strategies are queries on the service version graph that use the defined revision tags and the inter-version relationships to select the most appropriate service revision for users. A user may, for instance, define a selection strategy that always binds to the most recent revision in the graph, to the latest stable one, or to a revision belonging to a specific branch. Unlike one-time queries, this selection is monitored by the proxy – if the service version graph changes (for instance because of the insertion of a new revision) the result of the selection may also change, and the proxy may update its target service to reflect this change. We refer to this change in the proxies target service as dynamic rebinding. Dynamic rebinding is transparent to the client – it can be safely assumed that the most appropriate service according to the selection is invoked.

> VRESCO also supports the concept of revision tags. Tags may either be default tags with a well-defined meaning, or arbitrary strings. A list of default tags currently implemented is given in Table 1. Some of these default tags are assigned automatically by VRESCO (INITIAL, LATEST, HEAD) while others (STABLE, DEPREC, OFF) have to be assigned by the service provider

*  Interoperability Among Independently Evolving Web Services

> Interoperability with substituted services is non-trivial, however, and four types of incompatibilities may arise during such interoperation – structural, value, encoding and semantic. We address these incompatibilities three-fold: (1) static and dynamic analysis tools to infer whether an application is compatible with a substituted service, (2) semiautomatically generated middleware components called cross-stubs that actually resolve incompatibilities and enable interoperation with substituted services, and (3) a lightweight mechanism called multi-option types to enable applications to be written from the ground up in an interoperation-friendly manner.

> Given the service derivation scheme of the previous section, four types of incompatibilities may arise between applications and non-native services: structural, value, encoding and semantic. A structural incompatibility is a mismatch in the structure of the (XML) message sent by the sender and expected by the receiver, while a value incompatibility arises when the structure is as expected, but the filled-in values are unexpected. The bulk of the paper deals with structural and value incompatibilities (together referred to as SV-incompatibilities), and they are explained in more detail below. Encoding incompatibilities, illustrated and addressed in section 4, arise because instances belonging to different schema types are not identical even if they have the same structure and identical values. As explained in the previous section, semantic incompatibilities arise when different vendors introduce extensions with identical syntax (i.e., same struc- ture and value) but differing meanings, and the problem can be alleviated by namespaces and facets as further discussed in section 7.

> Compatibility Based on Statically Inferred Usage Behavior We provide a tool CAT-S (compatibility analysis tool-static) that uses the usage tuples to eliminate irrelevant SV-incompatibilities between the source and target interfaces. Each incompatibility i is processed by CAT-S as follows depending on which category (among I1 − I8 from figure 3) it belongs to

* Putting the semantics into semantic versioning https://arxiv.org/pdf/2008.07069

> Our thesis is that a critical part of helping developers safely upgrade is by detecting changes to contract specifications and implementations. The question then arises: “What exactly is a contract, and how do we find them?” Of course, there are many ways to define contracts! While contracts are often thought of in terms of programming constructs (e.g. types, pre/post-conditions, etc) they equally apply at higher levels (e.g. REST APIs, protocols, etc) and lower levels (e.g. linking) as well as to non-technical artifacts (e.g. licenses). Contracts can cover both functional and non-functional requirements— a significant degradation in the performance of a library might be considered a contract violation. Finally, contracts may be explicit (e.g. method foo() returns a List) or implicit (e.g. suggested by a method name such as export()).

> Contracts can help both upstream and downstream developers. From the upstream perspective, the constraints imposed by the contract actually represent freedom to change what is not in the contract. Behavioural properties not mentioned in the contract may be changed. Of course, the provider of an upstream component must preserve behaviour that is mentioned in the contract, or else explicitly amend the contract. Non-functional properties may be more fraught: there may be legitimate but undocumented expectations about performance, for instance. From the downstream perspective, unchanged contracts, along with tools to guarantee conformance to those contracts, can give developers more confidence that new versions are safe to upgrade to; differences between contracts point out where adaptation is needed.

> Formal contract inference. The traditional problem ofspecification inference —that is, the automatic inference of preand post-conditions—from legacy code has been studied extensively [Cousot et al. 2011; Polikarpova et al. 2009]. Indeed, Leino [2001] argues this is crucial to enabling more widespread uptake of verification technology: “For programming teams with large amounts of already written code, the initial investment of adding annotations to the legacy code seems daunting.”

> Most approaches to this problem are based on some combination of inferring weakest preconditions and strongest postconditions [Barnett and Leino 2005; Dijkstra 1976]. SnuggleBug is a salient example which employs a range of techniques [Chandra et al. 2009]. For example, it interleaves symbolic analysis with call graph construction to yield a more precise construction, and employs generalization to ensure specifications contain only “pertinent” information. 

> Program documentation (using natural language processing techniques) is also a source of program properties; for instance, Yang et al. [2018] extract endpoints from documentation of web APIs. Such approaches also work for extracting models from documentation [Zhai et al. 2016] or from code comments.

> Specification inference can also extract properties from program executions as in Daikon [Ernst 2000]. The work of McCamant and Ernst [2003] was particularly foresighted and relevant here: they developed an analysis based on dynamic invariant detection for predicting component upgrade problems in the context of a particular client. This essay proposes a research programme which is broader than that work on a number of axes: among others, we include the unknown-client case; propose the use of static and hybrid analyses; and point out the importance of non-behavioural properties.

> Lightweight contract inference. While inferring full specifications might be considered an ideal (in some sense), such specifications are expensive and fail to realize their full benefits without tools which can statically check them. As a result, much work has focused on inferring properties that can be viewed either as limited contracts or extended type systems. For example, researchers have developed tools that infer non-null annotations [Ekman and Hedin 2007] (in a world without Non-Null by Default) and ownership annotations [Dymnikov et al. 2013; Flanagan and Freund 2007; Huang et al. 2012; Milanova and Liu 2009].

> Focussing on a single client at a time, the work of Mezzetti et al. [2018], which introduces type regression testing, helps upstream developers avoid creating breaking changes in their node.js libraries. They leverage the known dependencies of the library under analysis and use the dependencies’ test cases to build a model of that library—in particular, of how the library is actually used downstream. Then, comparing models before and after a change detects changes that are breaking with respect to one client. Looking across clients, Mujahid et al. [2020] pool tests from a range of clients to determine whether a particular library change is generally breaking.

> Incremental and scalable static analysis. As software lifecycle iterations become ever shorter and programs ever larger, novel static analysis techniques have been deployed to make timely analysis possible. The elegant solution is to incrementalize—moving from computing results from scratch on each analysis run to updating the static analysis models and reading results from the models. New techniques to incrementalize are emerging for static analysis frameworks like Doop [Bravenboer and Smaragdakis 2009], bddbddb [Whaley et al. 2005], and Flix [Madsen et al. 2016] which are based on Datalog-based representations. The commercial Semmle tools also employ Datalog (QL)34. In Datalog, adding information and reading off new incremental results is trivial, as the fixpoint can be easily recomputed.

> The situation is significantly more complex when information has to be retracted. There is recent research in this space, with the incremental DDlog engine recently becoming available [Ryzhyk and Budiu 2019]. The Doop repository contains an experimental analysis based on DDlog35. There is active work to add incremental computation to Soufflé, the default engine used by Doop [Zhao et al. 2019]. As another, particularly relevant, example, the Facebook Infer tool [O’Hearn et al. 2017] performs inference and interprocedural verification of program properties that can be viewed as extended types, including nullness and resource leaks. It uses a compositional shape analysis [Calcagno et al. 2011]. Infer is extremely scalable—it runs quickly enough even on codebases with up to tens of millions of lines—even though it performs an inter-procedural analysis. One key to its scalability is its use of incremental static analysis: it records analysis information on each run and reuses this information on subsequent runs. Infer shows that (with sufficient engineering effort) such tools have the potential to be usable on industrial-sized codebases.

> High-recall static analysis. Traditionally static analysis has focused on balancing precision and scalability. More recently, researchers have turned their focus to recall or soundness, i.e. addressing issues around false negatives [Livshits et al. 2015]. Sui et al. [2020] have demonstrated the importance of this—standard call graph construction algorithms suffer from significant numbers of false negatives, undermining the utility of graph- and points-to-based analyses.

> Moreover, there are multiple sources of unsoundness, each having a significant impact, while research has focused on only one category (reflection) [Livshits et al. 2005; Smaragdakis et al. 2015].

> Our interest in this essay is in detecting breaking changes. Recall is relevant to this application because a sound, or at least a high-recall, analysis means that there are either no issues being missed, or that the number of issues that are being missed is reduced to an acceptable level. This can give users enough confidence to use tools to detect compatibilityrelated bugs. High-recall tools avoid or minimize chances for expensive runtime errors caused by undetected bugs, and the corresponding need to roll back upgrades.

> Recent progress in this field has focused on two areas: modelling of various dynamic language features in pure static analyses [Fourtounis et al. 2018; Fourtounis and Smaragdakis 2019], and hybrid analyses blending information gathered from program runs (via stack sampling, instrumentation, or heap snapshots) into static analyses [Bodden et al. 2011; Grech et al. 2017].

> We advocate for the use of data provenance, as defined in [Buneman et al. 2001]: “where a piece of data came from and the process by which it arrived in the database”. Currently, in semantic versioning, upstream developers provide a version number, a set of code changes, and perhaps a textual changelog. We envision a future where upstream developers provide, along with the version number, metadata encoding the reasoning behind the choice of that number, as supported by output from a versioning calculator (possibly stored in a database). In this future, downstream developers can use the provenance information to (1) establish trust in a versioning scheme, and (2) help them to assess where additional verification checks for a particular client should be performed

> changelog. We envision a future where upstream developers provide, along with the version number, metadata encoding the reasoning behind the choice of that number, as supported by output from a versioning calculator (possibly stored in a database). In this future, downstream developers can use the provenance information to (1) establish trust in a versioning scheme, and (2) help them to assess where additional verification checks for a particular client should be performed

* Using Others’ Tests to Identify Breaking Updates

* On the recall of static call graph construction in practice


* Type Regression Testing to Detect Breaking Changes in Node.js Libraries

> (1) Public API Discovery In the first phase, all the packages with tests that depend on the old library version are retrieved from npm

> Then, a public API model of both the old and the new library version is built using an instrumented interpreter that runs the tests of all the collected dependents. A model π, which we formally define in Section 5, is a map from dynamic access paths to types.

> (2) Type Regression Detection In the second phase, we compare the models π and π 0 obtained from the old and the new library version to report type regressions, which are indications of type-related breaking changes. Type regressions are detected by comparing π(p) and π 0 (p) for every dynamic access path p, using a notion of subtyping

* A catalogue of inter-parameter dependencies in RESTful web APIs http://personal.us.es/sergiosegura/files/papers/martinlopez19-icsoc.pdf

* Towards User-Friendly Projectional Editors https://sjmulder.nl/dl/pdf/unsorted/2014%20-%20Voelter%20et%20al%20-%20Towards%20User-Friendly%20Projectional%20Editors.pdf

* Inca A DSL for the Definition of Incremental Program Analyses https://www.pl.informatik.uni-mainz.de/files/2019/04/inca-incremental-analysis.pdf

* Incrementalizing lattice-based program analyses in Datalog https://dl.acm.org/doi/pdf/10.1145/3276509

* Query, analysis, and benchmarking techniques for evolving property graphs of software systems https://repozitorium.omikk.bme.hu/bitstream/handle/10890/13133/ertekezes.pdf?sequence=2

* Formal validation and model generation for domain-specific languages by logic solvers https://uwspace.uwaterloo.ca/bitstream/handle/10012/16088/Anbarnam_Davood.pdf?sequence=3&isAllowed=y

* On the Effectiveness of Incremental Fact Extraction and Analysis https://uwspace.uwaterloo.ca/bitstream/handle/10012/16088/Anbarnam_Davood.pdf?sequence=3&isAllowed=y

>  Fact Extraction is one such static analysis technique that extracts a base model of the underlying software containing properties of the system entities (e.g., variables, functions, files/classes) and their relationships, and stores them in the form of a database of facts (factbase). This base model can then be queried and analysed by developers to reveal higher-level design information, such as dataflow between various modules of a software system. Currently, approaches to building system models scale fairly well to large single systems; factbases can be created using time and resources comparable to that of the compilation process. However, software systems evolve over time, and these analyses need to be redone as the source code changes. While incremental compilation techniques have the potential to greatly reduce the time taken to rebuild the systems themselves, as yet there has been little research into tools that support incremental analysis of changing artifacts to produce revised factbases. This thesis proposes an extraction and analysis framework that is more amenable to creating models from changing artifacts: an Incremental Extraction and Analysis Framework. In particular, we focus on how changes at the file level - i.e., modifications to source files as well as the addition and removal of source files - can impact a previously extracted model and analysis. We evaluate our proposed framework by performing a case study on a build of the Linux Kernel. First, we compare two approaches to extracting a revised factbase from a new version of the build: one that uses a traditional approach and one that uses our proposed incremental extraction techniques. Then, we compare two approaches to analysing revised factbases: one that uses an incremental approach and one that does not. We found that significant performance improvements can be made in extracting a revised factbase when using an incremental approach, with extraction times being reduced by at least 50%, while re-analysing a revised factbase using an incremental approach grows linearly in terms of the number affected facts in the best case and follows an S-shaped growth in the worst case. We found that the cause for the observed exponential growth could be traced to a subset of facts, rather than being the result of a gradual increase of an analysis' search space.

> 2 Background & Related Work 6
> * 2.1 Fact Extraction as Compilation . . . . . . . . . . . . . . . . . . . . . . . . 6
> * 2.2 Factbases as Property Graphs . . . . . . . . . . . . . . . . . . . . . . . . . 9
> * 2.2.1 Tuple-Attribute Format . . . . . . . . . . . . . . . . . . . . . . . . 9
> * 2.2.2 Datalog . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
> * 2.3 Source Code Models as Property Graphs . . . . . . . . . . . . . . . . . . . 11

> Source Code Models as Property Graphs
> The practice of extracting a queryable model from source code artifacts is not new. Recent work in generating such models, however, are increasingly using the property graph model [39], using a tool such as Neo4j. Yamaguchi et al. used the property graph model to discover vulnerabilities in the Linux kernel [48]. To do so, they first modelled the code’s Abstract Syntax Tree, Control Flow Graph and Dependency Graph as property graphs, merging the separate representations into one code property graph. They then used graph traversal algorithms to find paths that matched specific vulnerability patterns using Apache Gremlin, detecting 18 new vulnerabilities. Goonetilleke et al. developed a code comprehension tool, Frappe, on top of Neo4j that maintained a versioned dependency graph of a system’s codebase, the main goal of the project being to aid developers in the code review process [21]. This versioned graph would allow developers to ask questions that could come up during code review, like which version saw the introduction of a new function or which version saw the addition of a new dependency, using graph traversal queries written in the Cypher query language [18]. Focusing on more niche systems, Pra ̈hofer et al. [37] used Static Analysis techniqu

> * 2.4 Fact Extraction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
> * 2.5 Incremental Model Extraction . . . . . . . . . . . . . . . . . . . . . . . . . 13
> * 2.6 Incremental Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13

> 3 Methodology 18
> * 3.1 The Naive Extraction Process (NEP) . . . . . . . . . . . . . . . . . . . . . 19
> * 3.2 The Incremental Extraction Process (IEP) . . . . . . . . . . . . . . . . . . 20
> * 3.2.1 Re-Extracting . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 23
> * 3.2.2 Diff & Replace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 23
> * 3.2.3 Update . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 24
> * 3.2.4 Creating Meta Facts . . . . . . . . . . . . . . . . . . . . . . . . . . 25
> * 3.3 The Naive Analysis Process (NAP) . . . . . . . . . . . . . . . . . . . . . . 27
> * 3.4 The Incremental Analysis Process (IAP) . . . . . . . . . . . . . . . . . . . 27
> * 3.4.1 Detecting Meta Facts . . . . . . . . . . . . . . . . . . . . . . . . . . 28
> * 3.4.2 Propagating Meta Facts . . . . . . . . . . . . . . . . . . . . . . . . 29
> * 3.4.3 Updating Analysis(Sys) . . . . . . . . . . . . . . . . . . . . . . . . 32
> * 3.5 Implementing the IEAP . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34

* Graph data management of evolving dependency graphs for multi-versioned codebases

> In this work we focus on the challenges associated with the management of multiple source code revisions, and investigate strategies to enable advanced code comprehension when the underlying codebase evolves over time. To find the deltas, we detail how entities can be resolved across versions, and propose a model for representing evolving dependency graphs.

> A ‘version’ or a ‘snapshot’ of the codebase is user-defined; incremental revisions to the code may be distinguished in terms of commits or an aggregated set of commits, and is generally associated with a revision number and/or a timestamp. Each new version of the source code produces a modified version of the dependency graph. In the rest of the document we use the terms version and snapshot interchangeably to refer to a particular point in time, either in the codebase or the corresponding dependency graph.

> We show growth and storage benefits of versioned graphs compared to independently storing individual snapshots. We also demonstrate how existing Frappe queries can be executed on ´ versioned graphs and new queries can retrieve a history of changes in a function for a code review use case.

* Lifting Datalog-Based Analyses to Software Product Lines https://arxiv.org/pdf/1907.02192.pdf

> Applying program analyses to Software Product Lines (SPLs) has been a fundamental research problem at the intersection of Product Line Engineering and software analysis. Different attempts have been made to "lift" particular product-level analyses to run on the entire product line. In this paper, we tackle the class of Datalog-based analyses (e.g., pointer and taint analyses), study the theoretical aspects of lifting Datalog inference, and implement a lifted inference algorithm inside the Soufflé Datalog engine. We evaluate our implementation on a set of benchmark product lines. We show significant savings in processing time and fact database size (billions of times faster on one of the benchmarks) compared to brute-force analysis of each product individually.

* Variability-Aware Datalog https://arxiv.org/pdf/1912.03854.pdf

> Variability-aware computing is the ability to efficiently compute over values from different worlds at the same time. A set of worlds is defined in terms of a set of features F. A world is defined by a configuration ρ, where each feature can be either present or absent. A set of worlds is defined by a propositional formula over features. Each software artifact can be labeled with a Presence Condition (PC): a propositional formula specifying the set of worlds in which this artifact exists. Datalog facts are an example of artifacts.

* Scalable, Example-Based Refactorings with Refaster https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/41876.pdf

> We discuss Refaster, a tool that uses normal, compilable before-and-after examples of Java code to specify a Java refactoring. Refaster has been used successfully by the Java Core Libraries Team at Google to perform a wide variety of refactorings across Google’s massive Java codebase. Our main contribution is that a large class of useful refactorings can be expressed in pure Java, without a specialized DSL, while keeping the tool easily accessible to average Java developers.

* API Parameter Recommendation Based on Documentation Analysis https://uwspace.uwaterloo.ca/bitstream/handle/10012/15506/Xi_Yuan.pdf?sequence=3&isAllowed=y

* A First Look at the Deprecation of RESTful APIs: An Empirical Study https://arxiv.org/pdf/2008.12808.pdf

> —REpresentational State Transfer (REST) is considered as one standard software architectural style to build web APIs that can integrate software systems over the internet. However, while connecting systems, RESTful APIs might also break the dependent applications that rely on their services when they introduce breaking changes, e.g., an older version of the API is no longer supported. To warn developers promptly and thus prevent critical impact on downstream applications, a deprecated-removed model should be followed, and deprecationrelated information such as alternative approaches should also be listed. While API deprecation analysis as a theme is not new, most existing work focuses on non-web APIs, such as the ones provided by Java and Android. To investigate RESTful API deprecation, we propose a framework called RADA (RESTful API Deprecation Analyzer). RADA is capable of automatically identifying deprecated API elements and analyzing impacted operations from an OpenAPI specification, a machine-readable profile for describing RESTful web service. We apply RADA on 2,224 OpenAPI specifications of 1,368 RESTful APIs collected from APIs.guru, the largest directory of OpenAPI specifications. Based on the data mined by RADA, we perform an empirical study to investigate how the deprecatedremoved protocol is followed in RESTful APIs and characterize practices in RESTful API deprecation. The results of our study reveal several severe deprecation-related problems in existing RESTful APIs. Our implementation of RADA and detailed empirical results are publicly available for future intelligent tools that could automatically identify and migrate usage of deprecated RESTful API operations in client code

> Automatic Test Generation of REST APIs https://www.diva-portal.org/smash/get/diva2:1484205/FULLTEXT01.pdf

> Combinatorial testing, also known as t-way testing, is a method for software testing. Combinatorial testing can effectively detect failures that are triggered by the interactions of parameters in the software under test (SUT). The method consists of testing all possible discrete combinations for each pair of input parameters. It is generally too large to test all of the possible combinations in the SUT, therefore it is normal to use a type of chosen test vectors in order to faster test the system than by using an exhaustive method. This requires a well defined model of the test parameters and is critical in order to effectively perform combinatorial testing

>  One of these open source tools is Tcases which is a model-based test case generator. The tool is primarily for designing black box test, thus the coverage criteria is instead guided from the input space of the system. With Tcases there is the possibility to define the input space for your system under test and the level of coverage that you want. Then Tcases will generate a minimal amount of test cases that meets the requirements specified. Tcases has the ability to generate test cases directly from a given OAS specification. The generated test cases, which are generated in the form of either YAML or JSON, can be seen as models from which actual tests can be generated. The generated tests provide enough information to be able to build tests that can guarantee that the minimum requirements of the system are covered, meaning that 100% coverage is guaranteed for the specified requirements.

* Consistent registration and discovery scheme for devices and Web service providers based on RAML using embedded RD in OCF IoT network https://www.mdpi.com/2071-1050/10/12/4706/pdf

> In this paper, a consistent registration and discovery scheme is proposed for the devices and web service providers in the Open Connectivity Foundation (OCF)-based IoT network. For supporting the proposed scheme, an embedded resource directory (RD) server is proposed to provide a consistent registration service that is used for publishing information of devices and web service providers. For the registration, a unified profile format is used that is based on the RESTful API Modeling Language to describes the information of devices and web service providers. Furthermore, the discovery service provides the consistent interface to discover the registered devices and web service providers by the client using the unified user interface. Accordingly, the client can access the resources of devices and web service providers based on the discovered information.

* Type-Safe Evolution of Web Services https://docentes.fct.unl.pt/sites/default/files/jmc-cunha/files/main_1.pdf

> In this paper, we present a programming model that allows the development of web service applications, server end-points and their clients, in such a way that the evolution of services’ implementation does not cause the disruption of the client. Our approach is based on a type based code slicing technique that ensures that each version only refers to type compatible code, of the same version or of a compatible version, and that each client request is redirected to the most recent type compatible version implemented by the server. We abstract the notion of version and parametrize type compatibility on the relation between versions. The relation between versions is tagged with compatibility levels, so to capture the common conventions used in software development. Our implementation allows multiple versions of a service to be deployed simultaneously, while reusing code between versions in a type safe way. We describe a prototype framework, based on code transformation, for server-side JavaScript code, and using Flow as verification tool.

* Typing the Evolution of Variational Software https://repositorium.sdum.uminho.pt/bitstream/1822/68173/1/TYPES18.pdf

> Maintaining multiple versions of a software system is a laborious and challenging task, which is many times a strong requirement of the software development process. Such hurdle is justified by needs of backward compatibility with libraries or existence of legacy equipment with particular constraints. It is also an intrinsic requirement of software product lines that target multiple target platforms, service, or licensing levels

> Another issue regarding variability is the evolution of software. Arguably, existing languagebased analysis tools for service orchestrations do not really account for evolution [14]. Nevertheless, there are other language- and type-based approaches that focus on dynamic reconfiguration and evolution of software [3, 4], hot swapping of code [10], and variability of software [5], that complement the evolution process with tools, and ensure that each version is sound. However, related versions of a software system usually share a significant amount of code, and there are no true guaranties of the sound co-existence of versions and sound transitions between versions at runtime. Such a need is relevant for monolithic software that must provide different versions in the same code base, and it is crucial in the context of service-based architectures. We have presented prior work to check the soundness of service APIs and the runtime transition between versions [2]. However, special hand crafted code was needed to maintain the semantic coherence of the versions of the state. Hence, we believe that the potential impact of a language-based tool supporting variability and a sound co-existence of versions is very high. By checking incremental evolution development it provides gains in safety and increases developer productivity.

* A Versioned Approach to Web Service Evolution https://run.unl.pt/bitstream/10362/20620/1/Campinhos_2017.pdf

> Applications based on micro-services or web services have had a significant growth due to the exponential increase in the use of mobile devices whose applications rely almost entirely on this type of interfaces. However, using an external interface comes with no guarantees to the developers using it. Changes may be introduced at any moment, which can break the software that is using those APIs. It is necessary to give the consumers guarantees that their software will not break, but not at the expense of stagnating the development of said web service. In this document we present a programming model to evolve web services in a sustainable way and to automate most of the maintainability that might be required by the consumer. This model works by allowing multiple versions to be deployed, and then using a relation containing metadata to type check versions. By doing this, it is possible to guarantee type safety between all the versions to provide a sustainable way to evolve the service. A prototype framework was implemented in JavaScript, where it is possible to visualize the model working in an environment similar to what it is used in the industry nowadays.

> RIDDL is an XML-based language used to incrementally compose REST APIs documentation by adding a changelog of the older version

> The example above is a Web API description annotated with hRESTS. To give further explanation, we will break down each of the definitions. service class Indicates that the following HTML block is an hRESTS element, containing a Web service or API description. operation class is used to indicate that the following block is a description of a Web service or API operation, meaning that it will have an address and method classes. address class specifies the URI of the operation and can be used on a textual element (the URI is the content) or on an anchor (the URI is the target). method class if used on a textual element (<span> for example), and represents the HTTP verb used on the operation (GET POST PUT . . . ) input and output classes are used to identify the operation’s input and output. While this provides useful information, it is not translated as a machine-readable information. label class is used to specify a human-readable label for a service, operation or message.
 
 > 2.1.6 RESTdesc RESTdesc is another specification for describing RESTful Web APIs where they are described using pre and post conditions [29]. RESTdesc uses the semantic web [30] as the base of its solution. Using RESTdesc we can create a descriptor using Notation3 [28], which is a language based on the core language for Semantic Web. The main elements of this descriptor are preconditions, which indicate the state a certain resource should have before the interaction, postconditions, which describe the new state of the resource, and request details, which explain which HTTP request should be made
 
* The Choice Calculus: A Representation for Software Variation http://web.engr.oregonstate.edu/~erwig/papers/ChoiceCalculus_TOSEM11.pdf
 
 > Many areas of computer science are concerned with some form of variation in software—from managing changes to software over time, to supporting families of related artifacts. We present the choice calculus, a fundamental representation for software variation that can serve as a common language of discourse for variation research, filling a role similar to the lambda calculus in programming language research. We also develop an associated theory of software variation, including sound transformations of variation artifacts, the definition of strategic normal forms, anda design theory for variation structures, which will support the development of better algorithms and tools.
 
 > The goal of our representation is to provide a formal model to represent variationin all kinds of languages and documents. To this end, we employ a simple tree model to represent the underlying artifact. This allows us to focus on the variational aspects of the representation, while providing a general and structured model to build on.
 
 > The fundamental concept of our representation is that of choice. A choice is a set of alternative expressions from which one can be selected. This selection can be facilitated by associating tags with each alternative expression in the choice; one then selects a tag to replace a choice with the corresponding alternative. There are (at least4 ) two ways to implement this association of alternatives and tags.

> (1) A choice is represented as a mapping from tags to alternative expressions. We call this the direct tagging approach.
> (2) The introduction of tags and their association with expressions are separated. Since the separate introduction of the tags amounts to the definition of a dimension of variation, we call this the dimension approach.

> For the choice calculus we have adopted the second, dimensioned approach because it provides a more structured representation, is more modular, and obeys a richer set of laws.

> There are two different ways of relating the choice calculus to the feature model view of variation management. The first is to consider the choice calculus primarily as a means of implementing feature models. This could be augmented by traditional feature modeling techniques or a higher-level “choice-model” that enforces additional, inter-dimensional constraints on selections applied to a choice expression. For example, one could specify that the selection of a tag in one dimension implies the selection of a tag in another, or that two particular tags in two differentdimensions cannot both be selected. The choice calculus compares favorably as an implementation strategy. Its use of an underlying tree model and local dimension declarations make it more structured than most annotation systems, but it is able to capture significantly finer-grained variation than FOP systems

* On the Origin of Services Using RIDDL for Description, Evolution and Composition of RESTful Services

> In this paper we want to introduce RIDDL, a flexible and extensible XML based language that not only allows to describe services but also covers the basic requirements of service composition and evolution to provide a clean foundation for further developments.

> This leads us to two important issues: service evolution and service composition. According to Kaminski et al. [3] the ultimate goal of service evolution is to permit change in the interface and implementation of a service while remaining backwards-compatible with clients written to comply with previous versions. Service composition is currently defined as the assembly of several services in a complex process [4], [5]. On the other hand a service itself may be a simple composition of several operations, maintained by different entities, operating on different datasets but exposed through a single interface. A RESTful service not just consists of a flat list of operations but of a tree of operations, therefore a simple composition can be a combination of multiple (possibly overlapping) resources.

* Automated Example Oriented REST API Documentation at Cisco

> In this research, we presented the results of using SpyREST at Cisco to maintain an up-to-date documentation with usage examples for an evolving REST API. Our primary findings provide an evidence that SpyREST can be used as a practical REST API documentation tool.

* Scalable Analysis of Variable Software https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.308.2100&rep=rep1&type=pdf

> The advent of variability management and generator technology enables users to derive individual variants from a variable
code base based on a selection of desired configuration options. 

> Variability-aware analysis (also known as family-basedanalysis [43]) takes advantage of the similarities between the variants of a system in order to speed up the analysis process. Although individual variability-aware analyses differ in many details [43], an idea that underlies all of them is to analyze code that is shared by multiple variants only once. To this end, variability-aware analyses do not operate on generated variants, but on the raw code artifacts that still contain variability and available configuration knowledge, prior to the variant-generation step

* Concepts of Variation Control Systems http://www.cse.chalmers.se/~bergert/paper/2020-jss-varcs.pdf

> We presented a classification of VarCS, which aim to integrate the management of revisions of software artifacts and the handling of software variants at different levels of granularity. Our study provides a classification of six VarCS and shows that they use concepts and approaches developed in the areas of both software configuration management and software product line engineering

* Principles of Feature Modeling

> Unfortunately, feature models are difficult to build and evolve. Features need to be identified, grouped, organized in a hierarchy, and mapped to software assets. Also, dependencies between features need to be declared. While feature models have been the subject of three decades of research, resulting in many feature-modeling notations together with automated analysis and configuration techniques, a generic set of principles for engineering feature models is still missing. It is not even clear whether feature models could be engineered using recurrent principles. Our work shows that such principles in fact exist. 

* Dynamically Discovering Likely Program Invariants https://asa.iti.kit.edu/daikon.pdf

* Early Identification of Incompatibilities in Multi-component Upgrades

* Model-Based Testing of Breaking Changes in Node.js Libraries

> This paper presents a model-based variant of type regression testing. Instead of comparing API models of a library before and after an update, it finds breaking changes by automatically generating tests from a reusable API model. Experiments show that this new approach significantly improves scalability: it runs faster, and it can find breaking changes in more libraries.

> An API model is a triple (π, σ, ρ). We first explainπ, which is map of the form π : Path → Type that associates types with elements of a library API. The set Path consists of dynamic access paths, each being a sequence of actions, as described in the following grammar by p and α, respectively.

* ARIANE : Automated Re-Documentation to Improve software Architecture uNderstanding and Evolution

> This re-documentation is performed from the analysis of both object-oriented code and project deployment descriptors. The re-documentation process targets the Dedal architecture language which is especially tailored for managing and driving software evolution. Another highly important aspect of software documentation relates to the way concepts are versioned. Indeed, in many approaches and actual version control systems such as GitHub, files are versioned in an agnostic manner. This way of versioning keeps track of any file history. However, no information can be provided on the nature of the new version, and especially regarding software backward-compatibility with previous versions. This thesis thus proposes a formal way to version software architectures, based on the use of the Dedal architecture description language which provides a set of formal properties. It enables to automatically analyze versions in terms of substitutability, version propagation and proposes an automatic way for incrementing version tags so that their semantics corrrespond to actual evolution impact.

* Intelligent REST API Data Fuzzing

## Future Direction

* QuickREST: Property-based Test Generation of OpenAPI-Described RESTful APIs https://arxiv.org/pdf/1912.09686

* Capturing and Enhancing In Situ System Observability for Failure Detection https://jaylorch.net/static/publications/panorama.pdf

* Logram: Efficient log parsing using n-gram dictionaries https://arxiv.org/pdf/2001.03038

* CrashTuner: detecting crash-recovery bugs in cloud systems via meta-info analysis

* Automatic Property-based Testing of GraphQL APIs

* A catalogue of inter-parameter dependencies in RESTful web APIs

* Generating an automated test suite by variable strength combinatorial testing for web services

* RestTestGen: automated black-box testing of RESTful APIs


## Tools

* a verification tool for weighted kripke graphs https://github.com/jonasfj/WKTool

> WKTool is a verification tool for weighted Kripke structures. It permits the specification of systems by the means of a CCS-like language. Properties are expressed using a weighted dialect of computation tree logic.

> The verification engine relies on fixed point computation on dependency graphs (See: Xinxin Liu, Scott A. Smolka: Simple Linear-Time Algorithms for Minimal Fixed Points). Queries may also be encoded in symbolic dependency graphs, which can be more efficient for large bounds. Moreover, the engine supports both global and on-the-fly exploration of the state-space.

* Pijul https://pijul.org/

> Pijul is a free and open source (GPL2) distributed version control system. Its distinctive feature is to be based on a sound theory of patches, which makes it easy to learn and use, and really distributed.

> https://pijul.com/model/#pushouts-and-distributed-algorithms

> Pijul commentary https://news.ycombinator.com/item?id=24592568
> Git rebase in depth https://news.ycombinator.com/item?id=19877811
> CRDT the hard parts https://news.ycombinator.com/item?id=23802208

* Optic domain engine https://github.com/opticdev/optic

* Unison Files https://www.cis.upenn.edu/~bcpierce/unison/

* Unison language https://www.unisonweb.org/

> Unison definitions are identified by content. Each Unison definition is some syntax tree, and by hashing this tree in a way that incorporates the hashes of all that definition's dependencies, we obtain the Unison hash which uniquely identifies that definition. This is the basis for some serious improvements to the programmer experience: it eliminates builds and most dependency conflicts, allows for easy dynamic deployment of code, typed durable storage, and lots more.

> https://news.ycombinator.com/item?id=22156370

* poetry version operators https://python-poetry.org/docs/versions/

* cargo yank https://doc.rust-lang.org/cargo/reference/publishing.html#cargo-yank

> commentary on diamond https://stephencoakley.com/2019/04/24/how-rust-solved-dependency-hell

* great expectations https://greatexpectations.io/
  * automated data profiling https://docs.greatexpectations.io/en/latest/reference/core_concepts/profilers.html#profilers
  * data expectations https://docs.greatexpectations.io/en/latest/reference/core_concepts/expectations/expectations.html#expectations
  * epectation glossary https://docs.greatexpectations.io/en/latest/reference/glossary_of_expectations.html#expectation-glossary
  * data docs https://docs.greatexpectations.io/en/latest/reference/core_concepts/data_docs.html#data-docs
  * data docs reference https://docs.greatexpectations.io/en/latest/reference/core_concepts.html#reference-core-concepts-data-docs
  * validation https://docs.greatexpectations.io/en/latest/reference/core_concepts/validation.html#validation

* DOOP framework java pointer analysis http://doop.program-analysis.org/

> Doop builds on the idea of specifying pointer analysis algorithms declaratively, using Datalog: a logic-based language for defining (recursive) relations. Doop carries the declarative approach further than past work (such as bddbddb) by describing the full end-to-end analysis in Datalog and optimizing aggressively through exposition of the representation of relations (for example indexing) to the Datalog language level.

* error prone java static analysis https://github.com/google/error-prone

> Error Prone …
> * hooks into your standard build, so all developers run it without thinking
> * tells you about mistakes immediately after they’re made
> * produces suggested fixes, allowing you to build tooling on it

* dependabot https://dependabot.com/

* swagger dsl https://github.com/intellinote/swagger-dsl

> A CoffeeScript-based domain-specific language for generating JSON documents for Swagger.

* blueprint https://apiblueprint.org/
  * https://github.com/apiaryio/curl-trace-parser

> A ... high-level API description language for web APIs.

* dredd https://github.com/apiaryio/dredd

> Dredd is a language-agnostic command-line tool for validating API description document against backend implementation of the API.

> Dredd reads your API description and step by step validates whether your API implementation replies with responses as they are described in the documentation.

* tcases https://github.com/Cornutum/tcases

> A model-based test case generator

* https://www.schemacrawler.com/

* Infer https://engineering.fb.com/2017/09/06/android/finding-inter-procedural-bugs-at-scale-with-infer-static-analyzer/

> Infer represents its summaries as specifications in a program logic. In more detail, a specification is a pair (pre,post) of a precondition and a postcondition

* revapi https://revapi.org/revapi-site/index.html

> Full featured API checker for Java and beyond.

* static analysis tools repo https://github.com/analysis-tools-dev/static-analysis

* restler https://github.com/microsoft/restler-fuzzer

> RESTler is the first stateful REST API fuzzing tool for automatically testing cloud services through their REST APIs and finding security and reliability bugs in these services.

* https://github.com/isa-group/RESTest

> RESTest is a framework for automated black-box testing of RESTful web APIs. It follows a model-based approach, where test cases are automatically derived from the OpenAPI Specification (OAS) of the API under test

* https://github.com/EMResearch/EvoMaster

> A tool for automatically generating system-level test cases. Currently targeting REST APIs.

* pythia https://github.com/mboehme/pythia

> Pythia provides statistical correctness guarantees for fuzzing campaigns (correctness), and quantifies how difficult it is to discover paths in a program (difficulty)

## Industry

* Conventional Commits https://www.conventionalcommits.org/en/v1.0.0/

> A specification for adding human and machine readable meaning to commit messages

* https://semver.org/

* Data Contract Versioning in WCF https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/data-contract-versioning

> * Breaking vs. Nonbreaking Changes
> * Adding and Removing Data Members
> * Required Data Members
> * Omitted Default Values

* Clojure Spec https://clojure.org/about/spec

* Formal Verification of Smart Contracts with the K Framework https://www.apriorit.com/dev-blog/592-formal-verification-with-k-framework

* Versioning in an Event Sourced System https://leanpub.com/esversioning/read

* rich hickey spec-ulation

http://blog.ezyang.com/2016/12/thoughts-about-spec-ulation-rich-hickey/

> While the problem of cascading version bumps is a real question that applies to semantic versioning in general, the "cascading version bumps" Rich is referring to in the Clojure ecosystem stem from a much more mundane source: best practices is to specify a specific version of a dependency in your package metadata. When a new version of a dependency comes out, you need to bump the version of a package so that you can update the recorded version of the dependency... and so forth.

* codemeta https://codemeta.github.io/

* https://www.opslevel.com/

> service ownership platform catalog everything have running in architecture

* https://konghq.com/kong-konnect#insomnia

* https://raml.org/

* https://swagger.io/solutions/api-testing/

* effx https://www.effx.com/

> * How do I get my data into effx?  How does that work?
> We provide various integrations to get your service data into effx. The primary method is via a YAML file you can drop within your Git repository. We have integrations with most Git providers to automatically lint and sync the information into effx when you push to your main (or master) branch. 
> Within our platform, you'll find our YAML builder where you can construct your YAML files using a helpful wizard and view changes to the YAML file in real-time before you commit to your code repository.
> For more information on our Git integrations, our effx-cli tool, and more, check out https://effx.com/help
> * How do you track service dependencies?
> Service dependencies can be defined in effx in two ways:
> - Integrations: we support most popular service mesh setups to automatically ingest and display your service dependencies
> - Via static configuration: we allow for dependencies to be defined within your YAML configuration.

* deepsource https://deepsource.io/

> granmarly for your code 


* https://meroxa.com/

* https://www.basedash.com/

* cloud custodian

Diff policies ci policies

* datafold 

Data diff

* dbt https://www.getdbt.com/

GitHub repo of sql

* clearly defined https://clearlydefined.io/about

Dependencies licenses https://crates.io/crates/cl-to-cd

* BMI discovery https://docs.bmc.com/docs/discovery/documentation-home-457408541.html

They get to install agents

* Spyrest http://www.spyrest.com/?from=@

SpyREST generates automated, customizable, version aware, and scenario based documentation for your REST API from real API calls

* https://apis.guru/openapi-directory/

> Our goal is to create a machine-readable Wikipedia for REST APIs with the following principals


## Oddshots

* EVM semantics https://github.com/kframework/evm-semantics

* Lean functional in place updates

> The Lean runtime implements the Perseus algorithm for functional in-place updating when possible. It's a very clever reimagining of reference counting from basic principles.

## Approach

Meaningful versioning is in the industry https://www.conventionalcommits.org/en/v1.0.0/

Formal models are in the industry https://github.com/elastic/elasticsearch-formal-models

What we propose should provide meaningful versioning and be verifiable as a formal model. To do this we need to define the properties we are interested in preserving.

### Key Questions

* how would I introduce changelog spec to an existing spec?
* can we solve the inference problem? (inferring most general scehma changelog from event stream)
* who am I breaking?

The viterbi algorithm should help https://en.wikipedia.org/wiki/Viterbi_algorithm

### Key Papers

* RESTest: Black-Box Constraint-Based Testing of RESTful Web APIs
* Resource and Dependency based Test Case Generation for RESTful Web Services
* On the Effectiveness of Incremental Fact Extraction and Analysis
* Web application development with third-party components
* End-to-End Versioning Support for Web Services 
* Interoperability Among Independently Evolving Web Services
* A First Look at the Deprecation of RESTful APIs
* Graph data management of evolving dependency graphs for multi-versioned codebases
* Towards Extracting Web API Specifications from Documentation
* Putting the Semantics into Semantic Versioning
* ARIANE: Automated Re-Documentation to Improve software Architecture uNderstanding and Evolution
* A Principled Approach to Version Control
* A Categorical Theory of Patches
* On the lattice of specifications: Applications to a specification methodology

### Data Driven

* real time traces
* api log ingestion?

### Formalism

Pushouts in category of fact operators

* Free conservative co-completion

* how does it handle application to code and behaviors?

### Dataset Examples

Nix packages represent versioned specs if we consider a fact language of only dependencies. Versions of packages differ by changing their dependencies. We can apply our reverse algorithm to generate a changelog spec from the Nix historical dataset.

### Demo

Given a stream of API events find the most general changelog describing it

* [demo](https://github.com/svanderbleek/changelog-spec-inference-demo)

### Criticism

Spec with name is enough in the Hickey model

## Strategy

json and rest are solved problems for ingestion and diffing

in a dependency graph spec conflicts represent breaking change

full automation, inference engine, formal behavior tracking, expansion eat ops level lunch

autodiscovery of formal models within a software project, model tracking, model breaking notifications, model management features, data defined contract inference

api monitoring? integrate with or compete with?

inject service mesh (istio.io)

relate to projectional editing

this is a form of program analysis, abstract evaluation of a spec accumulating function through incremental analysis

evolving property graphs of software systems

need to enable blob optimization of analysis don't need full contents

can [hash](https://hash.ai/) simulate companies depending on each others api releases

Does test automation  exercise api? We can injest 

Data sources: Log files, network topologies

Properties analyzed: versioning, dependency, security, change management, cost, licensing

API calls in cloud control plane, apis have audit log (custodian has subscribe and invoke policy, real-time using flight recording)

We can offer ide services based on knowledge of apis

### Categorical Databases

Specs are like schemas in category of databases, we are learning the migrations which are morphisms in category of schemas.

### Automation

Injesting logs would involve difficult automation as shown in Towards Extracting Web API Specifications from Documentation.

### Potential Difficulties

* distributed tracing
* namespacing, environemnts, existing versioning/release
* declared/discovered general injestion lattice definition and model building
* should apply to method calls of libraries as well as apis
* focus on existence information, fields, does generalize to other information reducers? Crdt?
* dependency alert propagation 
* support information flow from consumer and producer side
* sessions? api tokens?
* rails nested parameters
* meaning of error examples 404 500 
