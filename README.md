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
