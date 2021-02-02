# cqrs-hypergraph-spec-propagators

title is a joke, research dumping ground for formal models of api dependencies

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

## Research

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

* APIComposer: Data-driven composition of REST APIs https://modeling-languages.com/wp-content/uploads/2018/08/esocc2018.pdf

* REST API Auto Generation: A Model-Based Approach https://www.researchgate.net/profile/Samer_Zein/publication/344403957_REST_API_Auto_Generation_A_Model-Based_Approach/links/5f71dddba6fdcc0086438ed0/REST-API-Auto-Generation-A-Model-Based-Approach.pdf

* Semantic Restful Service Composition Using Task Specification

* Automated generation of client-specific backends utilizing existing microservices and architectural knowledge

* Towards better utilizing static application security testing https://www.cs.purdue.edu/homes/lintan/publications/priv-icse19.pdf

* Web application development with third-party components https://tel.archives-ouvertes.fr/tel-02101381/document

* Putting the semantics into semantic versioning https://arxiv.org/pdf/2008.07069

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

* Lifting Datalog-Based Analyses to Software Product Lines https://arxiv.org/pdf/1907.02192.pdf

> Applying program analyses to Software Product Lines (SPLs) has been a fundamental research problem at the intersection of Product Line Engineering and software analysis. Different attempts have been made to "lift" particular product-level analyses to run on the entire product line. In this paper, we tackle the class of Datalog-based analyses (e.g., pointer and taint analyses), study the theoretical aspects of lifting Datalog inference, and implement a lifted inference algorithm inside the Soufflé Datalog engine. We evaluate our implementation on a set of benchmark product lines. We show significant savings in processing time and fact database size (billions of times faster on one of the benchmarks) compared to brute-force analysis of each product individually.

* Variability-Aware Datalog https://arxiv.org/pdf/1912.03854.pdf

> Variability-aware computing is the ability to efficiently compute over values from different worlds at the same time. A set of worlds is defined in terms of a set of features F. A world is defined by a configuration ρ, where each feature can be either present or absent. A set of worlds is defined by a propositional formula over features. Each software artifact can be labeled with a Presence Condition (PC): a propositional formula specifying the set of worlds in which this artifact exists. Datalog facts are an example of artifacts.

## Future Direction

* QuickREST: Property-based Test Generation of OpenAPI-Described RESTful APIs https://arxiv.org/pdf/1912.09686

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

> content-adressable programming language

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

* dependabot https://dependabot.com/

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

### Potential Difficulties

* distributed tracing
* namespacing, environemnts, existing versioning/release
* declared/discovered general injestion lattice definition and model building
* should apply to method calls of libraries as well as apis
* focus on existence information, fields, does generalize to other information reducers? Crdt?
* dependency alert propagation 
