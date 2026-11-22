[![awesome-privacy-adtech](image/awesome-privacy-adtech.png)](https://github.com/adops-tool/awesome-privacy-adtech/pulls)

[![animated-line](https://github.com/readme-SVG/animated-line/blob/main/STORAGE/line-svg-3D444D.svg)](https://github.com/readme-SVG/animated-line) <!-- -SVG-Line- -->

**Open-source consent tooling, normative specifications, and privacy-enhancing technologies for engineers building ad-funded products that respect users.**

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg)](LICENSE)

---

A curated map of the privacy engineering surface for advertising systems: self-hostable CMPs, the IAB and W3C signals that carry user choice, the browser APIs that replaced (or failed to replace) third-party cookies, and the cryptographic machinery now used to compute on data nobody is allowed to see.

**Scope.** Preference is given to code you can run, specifications you can implement against, and reference implementations published by the standards bodies themselves. Purely commercial SaaS platforms are deliberately excluded, since what they publish is positioning rather than a mechanism you can inspect or implement.

**Currency note (November 2026).** This landscape moves fast and several long-standing assumptions no longer hold. Chrome has **deprecated and removed** Attribution Reporting, Protected Audience, Topics, Shared Storage, Private Aggregation, and Related Website Sets, and is phasing out Fenced Frames; the entries below are labelled accordingly because the designs remain the reference material for the wider industry. IAB Tech Lab renamed the **Global Privacy Platform** the **Global Privacy Protocol** (both abbreviated GPP) and renamed **Seller Defined Audiences** to **Curated Audiences**, while Apple's **Private Click Measurement** is now shipped as **Web AdAttributionKit**.

**Legend:** ![github](image/alg_R.png) GitHub resource · ![web](image/alg_I.png) website or published document.

## Table of Contents

- [1. Open-Source Consent Management Platforms (CMPs)](#1-open-source-consent-management-platforms-cmps)
- [2. Consent & Privacy Standards](#2-consent--privacy-standards)
- [3. Browser Privacy & Sandbox APIs](#3-browser-privacy--sandbox-apis)
- [4. Privacy-Enhancing Technologies (PETs) & Clean Rooms](#4-privacy-enhancing-technologies-pets--clean-rooms)
- [5. Alternative Identifiers & Cookieless Specs](#5-alternative-identifiers--cookieless-specs)
- [6. Auditing, Debugging & Compliance Tools](#6-auditing-debugging--compliance-tools)
- [7. Technical Reading & Working Groups](#7-technical-reading--working-groups)
- [Contributing](#contributing)
- [License](#license)

---

## 1. Open-Source Consent Management Platforms (CMPs)

*Self-hostable consent tools and UI components for collecting preferences and controlling scripts. Framework registration and deployment configuration are separate steps.*

### Consent Interfaces and Script Gating

![github](image/alg_R.png) [Klaro](https://github.com/kiprotect/klaro) - Consent manager that rewrites third-party script tags into inert placeholders and only materialises them after per-service opt-in.

![github](image/alg_R.png) [Orejime](https://github.com/empreinte-digitale/orejime) - Klaro-derived consent manager rebuilt around WCAG and French RGAA accessibility, with fully keyboard-navigable and screen-reader-announced dialogs.

![github](image/alg_R.png) [CookieConsent](https://github.com/orestbida/cookieconsent) - Dependency-free vanilla-JS consent plugin providing granular per-category preferences, multi-language UI, and a documented pre-consent script-blocking API.

![github](image/alg_R.png) [c15t](https://github.com/c15t/c15t) - Headless consent infrastructure for React, Next.js, and Vue with first-class IAB TCF and Google Consent Mode v2 adapters.

![github](image/alg_R.png) [tarteaucitron.js](https://github.com/AmauriC/tarteaucitron.js) - Service-level consent manager that maps each third-party widget to its own toggle and supports Google Consent Mode v2.

![github](image/alg_R.png) [Osano CookieConsent](https://github.com/osano/cookieconsent) - The long-maintained cookieconsent.js library for a compact EU/GDPR notice with theming and opt-in or opt-out modes.

![github](image/alg_R.png) [Silktide Consent Manager](https://github.com/silktide/consent-manager) - MIT-licensed banner driven by a JSON configuration and paired with a script-blocking layer that runs before consent.

![github](image/alg_R.png) [react-cookie-consent](https://github.com/Mastermindzh/react-cookie-consent) - Minimal cookie consent bar for React applications, useful as a UI primitive rather than a complete compliance layer.

![github](image/alg_R.png) [libreconsent](https://github.com/nicolasestrem/libreconsent) - Self-hosted consent library with tag gating, Google Consent Mode v2, and a read-only bridge to external TCF CMPs.

![github](image/alg_R.png) [Consenti](https://github.com/santoshe61/consenti) - Self-hosted consent toolkit with a frontend widget, optional backend, and partial TCF and GPP support.

## 2. Consent & Privacy Standards

*The wire formats and in-page APIs that carry consent between publishers, CMPs, and vendors. If you are decoding a string in a bid request, the normative text lives here.*

### IAB TCF — Transparency & Consent Framework

![web](image/alg_I.png) [IAB Europe TCF](https://iabeurope.eu/transparency-consent-framework/) - Governance home for the framework, currently v2.3, which makes the Disclosed Vendors segment mandatory to resolve legitimate-interest disclosure ambiguity.

![github](image/alg_R.png) [TCF technical specifications](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework) - Normative TC String encoding, CMP API (`__tcfapi`), Global Vendor List, and Global CMP List formats maintained by IAB Tech Lab.

![github](image/alg_R.png) [iabtcf-es](https://github.com/InteractiveAdvertisingBureau/iabtcf-es) - Official TypeScript TC String encoder/decoder plus the CMP API shim and GVL tooling that most registered CMPs are built on.

![github](image/alg_R.png) [iabtcf-java](https://github.com/InteractiveAdvertisingBureau/iabtcf-java) - JVM implementation of TC String encoding and decoding for server-side bidstream processing.

![github](image/alg_R.png) [iabconsent](https://github.com/LiveRamp/iabconsent) - Go parser for TCF v1.1 and v2 strings, convenient for high-throughput bidder and SSP pipelines.

### Global Privacy Protocol (GPP)

![github](image/alg_R.png) [Global Privacy Protocol specification](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform) - IAB Tech Lab multiplexing spec that carries TCF-EU, TCF-CA, the MSPA US National string, and individual state privacy strings in one payload via `__gpp`.

![github](image/alg_R.png) [GPP section registry](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections) - Canonical per-jurisdiction string definitions, the file to diff when a new state law lands.

![github](image/alg_R.png) [iabgpp-es](https://github.com/IABTechLab/iabgpp-es) - TypeScript GPP encoder/decoder and CMP API implementation for the v1.1 callback-based interface.

![github](image/alg_R.png) [iabgpp-java](https://github.com/IABTechLab/iabgpp-java) - Java counterpart for GPP string encoding and decoding.

![github](image/alg_R.png) [iabgpp-rs](https://github.com/noirotm/iabgpp-rs) - Community Rust implementation of GPP string parsing for latency-sensitive services.

![github](image/alg_R.png) [go-gpp](https://github.com/prebid/go-gpp) - Go library for parsing IAB Global Privacy Protocol strings used by Prebid Server.

### Global Privacy Control (GPC)

![web](image/alg_I.png) [Global Privacy Control specification](https://www.w3.org/TR/gpc/) - W3C Working Draft defining the `Sec-GPC` request header and the `navigator.globalPrivacyControl` DOM property as an enforceable opt-out-of-sale-and-sharing signal.

![github](image/alg_R.png) [w3c/gpc](https://github.com/w3c/gpc) - Editor's draft, explainer, and issue tracker for GPC, now a W3C Privacy Working Group standards-track item.

![web](image/alg_I.png) [globalprivacycontrol.org](https://globalprivacycontrol.org/) - Implementer-facing home for GPC with browser and extension support status plus a reference server to test against.

## 3. Browser Privacy & Sandbox APIs

*What browsers actually enforce. Note that the Chrome ad-targeting stack was largely deprecated in 2025–2026, so these entries matter both as live implementation targets and as the documentary record of an architectural direction the industry abandoned.*

### Chrome Privacy Sandbox

![web](image/alg_I.png) [Privacy Sandbox overview](https://privacysandbox.google.com/) - Entry point to the API portfolio, now fronted by an explicit notice that several technologies are being phased out.

![web](image/alg_I.png) [Privacy Sandbox feature status](https://privacysandbox.google.com/overview/status) - Authoritative, continuously updated lifecycle table for every API — read this before designing against any of them.

![web](image/alg_I.png) [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) - On-device interest-group auctions intended to serve remarketing without cross-site identifiers, deprecated and removed from Chrome.

![github](image/alg_R.png) [TURTLEDOVE / FLEDGE explainer](https://github.com/WICG/turtledove) - Archived WICG design for in-browser ad auctions that was later specified as Protected Audience.

![web](image/alg_I.png) [Topics API](https://privacysandbox.google.com/private-advertising/topics) - Epoch-based, taxonomy-limited interest signal exposed through `document.browsingTopics()` and `Sec-Browsing-Topics`, deprecated and removed.

![github](image/alg_R.png) [Attribution Reporting API](https://github.com/WICG/attribution-reporting-api) - Archived proposal for event-level and aggregatable conversion reports, deprecated in Chrome.

![github](image/alg_R.png) [Aggregation Service](https://github.com/privacysandbox/aggregation-service) - TEE-hosted service that batches, decrypts, and noisily aggregates summary reports so no single operator sees both input and output.

![github](image/alg_R.png) [Fenced Frames](https://github.com/WICG/fenced-frame) - Embedding primitive that isolates ad content from the embedding page's DOM and storage, scheduled for removal.

### Browser Attribution Proposals

![web](image/alg_I.png) [Attribution Level 1](https://www.w3.org/TR/privacy-preserving-attribution/) - W3C working draft for aggregate advertising attribution using distributed aggregation and differential privacy.

### Partitioned Storage (cross-browser specs)

![github](image/alg_R.png) [CHIPS](https://github.com/privacycg/CHIPS) - The `Partitioned` cookie attribute, which keys storage by top-level site to block cross-site rejoining while preserving embedded flows, shipped in Chrome and adopted by WebKit's cookie policy.

![github](image/alg_R.png) [Storage Access API](https://github.com/privacycg/storage-access) - Spec letting embedded frames request access to their first-party cookies under an explicit user gesture, implemented in Chrome, Safari, and Firefox.

### Safari and WebKit

![web](image/alg_I.png) [Tracking Prevention in WebKit](https://webkit.org/tracking-prevention/) - Implementation-level description of ITP, including partitioned storage, the script-writable storage cap, and bounce-tracking defences.

![web](image/alg_I.png) [Introducing Private Click Measurement](https://webkit.org/blog/11529/introducing-private-click-measurement-pcm/) - Design rationale for 8-bit source and 4-bit trigger attribution with a randomised 24–48 hour reporting delay.

![github](image/alg_R.png) [Private Click Measurement specification](https://github.com/privacycg/private-click-measurement) - Privacy Community Group work item defining the attribution wire format and the `.well-known` trigger endpoints.

![web](image/alg_I.png) [Private Browsing 2.0](https://webkit.org/blog/15697/private-browsing-2-0/) - Documents Web AdAttributionKit in Private Browsing, link tracking parameter stripping, and partitioned session storage.

![web](image/alg_I.png) [AdAttributionKit](https://developer.apple.com/app-store/ad-attribution/) - Apple's app install and re-engagement attribution framework, using crowd-anonymity tiers to gate postback detail.

### Firefox

![github](image/alg_R.png) [Multi-Account Containers](https://github.com/mozilla/multi-account-containers) - Firefox extension that partitions cookies and site data per container, a user-controlled analogue of first-party-set storage isolation.

## 4. Privacy-Enhancing Technologies (PETs) & Clean Rooms

*The cryptographic and statistical substrate for computing aggregate answers over data that never leaves its owner's boundary.*

### Differential Privacy

![github](image/alg_R.png) [Google Differential Privacy](https://github.com/google/differential-privacy) - Production C++, Go, and Java libraries implementing Laplace and Gaussian mechanisms with rigorous privacy budget accounting.

![github](image/alg_R.png) [OpenDP](https://github.com/opendp/opendp) - Rust core with Python bindings exposing composable transformations and measurements under a formal privacy framework.

![github](image/alg_R.png) [SmartNoise SDK](https://github.com/opendp/smartnoise-sdk) - Differentially private query layer for SQL and Spark workloads with a policy-driven privacy accountant.

![github](image/alg_R.png) [Tumult Analytics](https://github.com/opendp/tumult-analytics) - Python library for privately computing aggregate queries on tabular data with explicit privacy loss tracking.

![github](image/alg_R.png) [Diffprivlib](https://github.com/IBM/differential-privacy-library) - IBM's scikit-learn-compatible library bringing DP guarantees to common ML estimators and statistics.

![github](image/alg_R.png) [TensorFlow Privacy](https://github.com/tensorflow/privacy) - DP-SGD optimizers and privacy accounting for training models without memorising individual records.

![github](image/alg_R.png) [PyDP](https://github.com/OpenMined/PyDP) - Python bindings over Google's C++ DP library for analysts who do not want to touch C++.

![github](image/alg_R.png) [Opacus](https://github.com/meta-pytorch/opacus) - PyTorch library for training models with differential privacy.

![github](image/alg_R.png) [PipelineDP](https://github.com/OpenMined/PipelineDP) - Python framework for differentially private aggregations on batch processing systems including Apache Beam and Spark.

### Secure Multiparty Computation

![github](image/alg_R.png) [MP-SPDZ](https://github.com/data61/MP-SPDZ) - Multi-protocol framework spanning arithmetic, binary, and garbled-circuit protocols with a common high-level language.

![github](image/alg_R.png) [MOTION](https://github.com/encryptogroup/MOTION) - C++ MPC framework with a modular front end for composing mixed-protocol two-party and multi-party computations.

![github](image/alg_R.png) [SecretFlow](https://github.com/secretflow/secretflow) - Unified Python framework combining MPC, TEE, and federated learning under one programming model.

![github](image/alg_R.png) [libscapi](https://github.com/cryptobiu/libscapi) - Comprehensive C++ library of secure two-party and multi-party computation protocols and primitives.

![github](image/alg_R.png) [MPZ](https://github.com/privacy-scaling-explorations/mpz) - Rust library of maliciously secure two-party and three-party MPC primitives designed for embedded use.

### Private Set Intersection

![github](image/alg_R.png) [OpenMined PSI](https://github.com/OpenMined/PSI) - ECDH plus Bloom filter private set intersection cardinality protocol with C++, Go, and Python bindings.

![github](image/alg_R.png) [libPSI](https://github.com/osu-crypto/libPSI) - Research-grade PSI and private set union protocols built for very large input sets.

![github](image/alg_R.png) [SecretFlow PSI](https://github.com/secretflow/psi) - PSI and private information retrieval implementations extracted from the SecretFlow project.

![github](image/alg_R.png) [Private Join and Compute](https://github.com/google/private-join-and-compute) - Cryptographic protocol implementation for calculating aggregate statistics over the intersection of two private datasets.

### Trusted Execution and Encryption

![github](image/alg_R.png) [Microsoft SEAL](https://github.com/microsoft/SEAL) - Homomorphic encryption library implementing the BFV and CKKS schemes for arithmetic directly on ciphertext.

![github](image/alg_R.png) [Confidential Consortium Framework](https://github.com/microsoft/CCF) - Framework for building attested, ledger-backed confidential services inside hardware enclaves.

![github](image/alg_R.png) [Open Enclave SDK](https://github.com/openenclave/openenclave) - Portable, vendor-neutral enclave abstraction for writing TEE applications once and running them across platforms.

![github](image/alg_R.png) [OpenFHE](https://github.com/openfheorg/openfhe-development) - C++ library implementing homomorphic encryption schemes and operations on encrypted data.

![github](image/alg_R.png) [TenSEAL](https://github.com/OpenMined/TenSEAL) - Python library for homomorphic encryption operations on tensors using Microsoft SEAL.

![github](image/alg_R.png) [Apache Teaclave](https://github.com/apache/teaclave) - Platform for confidential computing on sensitive data using trusted execution environments.

### Aggregation and Measurement Primitives

![github](image/alg_R.png) [libprio-rs](https://github.com/divviup/libprio-rs) - Rust implementation of the Prio secret-shared aggregation scheme that underpins privacy-preserving telemetry.

![github](image/alg_R.png) [Janus](https://github.com/divviup/janus) - Server implementation of the Distributed Aggregation Protocol (DAP) for splitting trust between two aggregators.

### Clean Room Standards

![github](image/alg_R.png) [Data Clean Rooms Guidance](https://github.com/InteractiveAdvertisingBureau/Data-Clean-Rooms) - IAB Tech Lab baseline expectations, threat models, and operating practices for clean room deployments.

![github](image/alg_R.png) [PAIR](https://github.com/InteractiveAdvertisingBureau/PAIR) - Publisher Advertiser Identity Reconciliation protocol using commutative encryption to match first-party identifiers across parties without cleartext exchange.

![github](image/alg_R.png) [ADMaP](https://github.com/InteractiveAdvertisingBureau/ADMAP) - Attribution Data Matching Protocol combining PSI and TEEs to measure conversions across publishers without revealing user-level data.

![web](image/alg_I.png) [IAB Tech Lab Differential Privacy Guide](https://iabtechlab.com/differential-privacy/) - Practitioner-oriented treatment of applying DP to targeting and attribution, including the privacy-versus-utility trade-off.

![github](image/alg_R.png) [FBPCS](https://github.com/facebookresearch/fbpcs) - Meta's MPC-based private computation service for ads measurement, archived as a worked reference architecture.

### Privacy-Conscious Analytics

![github](image/alg_R.png) [Matomo](https://github.com/matomo-org/matomo) - Self-hostable web analytics platform with configurable privacy and data retention settings.

![github](image/alg_R.png) [Plausible](https://github.com/plausible/analytics) - Web analytics application that supports cookie-free traffic and conversion measurement.

![github](image/alg_R.png) [Umami](https://github.com/umami-software/umami) - Self-hostable web analytics application for traffic, events, and conversions without tracking cookies.

Analytics configuration and applicable consent requirements vary by deployment and jurisdiction.

## 5. Alternative Identifiers & Cookieless Specs

*Proposals for addressability that survive without third-party cookies — and the plumbing that decides whether they are allowed to fire.*

### Unified ID 2.0

![github](image/alg_R.png) [Unified ID 2.0 documentation](https://github.com/IABTechLab/uid2docs) - Specification, integration guides, and operator runbooks for the UID2 ecosystem.

![github](image/alg_R.png) [uid2-shared](https://github.com/IABTechLab/uid2-shared) - Shared Java libraries covering token generation, encryption, and salt handling across UID2 services.

![github](image/alg_R.png) [uid2-operator](https://github.com/IABTechLab/uid2-operator) - Self-hostable UID2 Operator that runs inside your own cloud account under your own attestation boundary.

![github](image/alg_R.png) [uid2-web-integrations](https://github.com/IABTechLab/uid2-web-integrations) - Client-side SDK for obtaining, refreshing, and retiring UID2 tokens in web environments.

### PAIR and Curated Audiences

![web](image/alg_I.png) [Curated Audiences (formerly Seller Defined Audiences)](https://iabtechlab.com/sda/) - IAB Tech Lab standard for signalling taxonomised first-party audience segments in OpenRTB without cookies or user identifiers.

![web](image/alg_I.png) [PAIR protocol website](https://iabtechlab.com/pair/) - Overview and release history for the v1.1 protocol, including the Prebid module that implements it.

![github](image/alg_R.png) [OpenRTB 2.x](https://github.com/InteractiveAdvertisingBureau/openrtb2.x) - Normative home of the bid request and response object model through which all of these signals travel.

![github](image/alg_R.png) [OpenRTB community extensions](https://github.com/InteractiveAdvertisingBureau/openrtb/tree/master/extensions/community_extensions) - Registry of extension objects for audience segments, DSA transparency, and ID support that Curated Audiences and PAIR depend on.

### Prebid and Server-Side Plumbing

![github](image/alg_R.png) [Prebid.js user ID modules](https://github.com/prebid/Prebid.js/tree/master/modules/userId) - Reference implementations of identity submodules alongside the eids and consent plumbing that gates them.

![github](image/alg_R.png) [Prebid Server](https://github.com/prebid/prebid-server) - Server-side header bidding implementation, useful for moving identity resolution and consent checks out of the browser.

![github](image/alg_R.png) [SharedID](https://github.com/prebid/Shared-Id) - Prebid's donated shared cookie namespace with an opt-out and TCF-aware consent handling.

![github](image/alg_R.png) [Trusted Server](https://github.com/InteractiveAdvertisingBureau/Trusted-Server) - IAB Tech Lab's Rust-to-Wasm edge runtime that gives publishers a durable first-party context at the CDN perimeter instead of in the browser.

![web](image/alg_I.png) [Prebid.js module overview](https://docs.prebid.org/dev-docs/modules/index.html) - Documentation for Prebid.js modules, including TCF and GPP consent management and privacy controls.

![github](image/alg_R.png) [Prebid Server Java](https://github.com/prebid/prebid-server-java) - Java implementation of Prebid Server with support for server-side auction and privacy signals.

## 6. Auditing, Debugging & Compliance Tools

*Instrumentation for the question that actually matters in an audit: what fired, on whose behalf, and was there consent for it.*

### Site and Consent Auditing

![github](image/alg_R.png) [OpenWPM](https://github.com/openwpm/OpenWPM) - Research platform for instrumenting browsers at crawl scale to measure tracking, storage writes, and script behaviour reproducibly.

![github](image/alg_R.png) [webXray](https://github.com/thezedwards/webXray) - Analysis tool that resolves third-party requests on a crawl to the corporate owners actually receiving the data.

![github](image/alg_R.png) [Blacklight](https://github.com/the-markup/blacklight-collector) - Real-time site inspector from The Markup that detects cookies, keystroke capture, session replay, and canvas fingerprinting on a given URL.

### Browser Extensions and Consent Automation

![github](image/alg_R.png) [CookieBlock](https://github.com/dibollinger/CookieBlock) - Classifier-driven extension that evaluates each cookie's purpose and removes those not required by the visited site.

![github](image/alg_R.png) [Consent-O-Matic](https://github.com/cavi-au/Consent-O-Matic) - Rule-driven extension that answers consent banners according to a stored user preference instead of a site's defaults.

![github](image/alg_R.png) [DuckDuckGo autoconsent](https://github.com/duckduckgo/autoconsent) - Shared, CMP-agnostic rule library used to detect and auto-reject cookie prompts, embedded in DuckDuckGo and Firefox.

![github](image/alg_R.png) [uBlock Origin](https://github.com/gorhill/uBlock) - Wide-spectrum content blocker whose filter syntax has become the de facto contract for ad and tracker endpoints.

![github](image/alg_R.png) [Privacy Badger](https://github.com/EFForg/privacybadger) - EFF's behavioural blocker that learns which domains track you across sites and honours the GPC and DNT signals.

![github](image/alg_R.png) [Ghostery Extension](https://github.com/ghostery/ghostery-extension) - Tracker-blocking extension with an open-source detection engine and per-site reporting built on the same rule sets.

### Databases and Diagnostic Utilities

![github](image/alg_R.png) [Open Cookie Database](https://github.com/jkwakman/Open-Cookie-Database) - Community CSV catalogue of cookie names, durations, and purposes that scanners and CMPs consume as ground truth.

![web](image/alg_I.png) [IAB GPP encoder/decoder](https://iabgpp.com/) - Hosted tool for decoding and re-encoding GPP, TCF-EU, TCF-CA, and US state strings.

![github](image/alg_R.png) [Privacy Sandbox Analysis Tool](https://github.com/GoogleChromeLabs/ps-analysis-tool) - Archived Chrome extension and CLI that inventories cookies and maps them to Privacy Sandbox API usage.

![github](image/alg_R.png) [gdpr-cookie-scanner](https://github.com/Slashgear/gdpr-cookie-scanner) - Command-line scanner that compares cookies and network requests before and after consent interactions.

![github](image/alg_R.png) [consentdiff](https://github.com/Elijas121/consentdiff) - Browser-based scanner that compares third-party requests and cookies before consent and after accept or reject.

![github](image/alg_R.png) [Presidio](https://github.com/data-privacy-stack/presidio) - Framework for detecting and redacting personal information in text, images, and structured data.

![github](image/alg_R.png) [PrivacyTests](https://github.com/privacytests/privacytests) - Browser test suite and website comparing privacy protections across browsers.

### Tracker Databases and Blocking Engines

![github](image/alg_R.png) [DuckDuckGo Tracker Radar](https://github.com/duckduckgo/tracker-radar) - Dataset of third-party web domains with ownership and tracking metadata.

![github](image/alg_R.png) [Disconnect Tracking Protection](https://github.com/disconnectme/disconnect-tracking-protection) - Repository of categorized third-party services used for tracking protection.

![github](image/alg_R.png) [Ghostery TrackerDB](https://github.com/ghostery/trackerdb) - Database of trackers and associated metadata used by Ghostery.

![github](image/alg_R.png) [EasyList](https://github.com/easylist/easylist) - Source repository for filter lists including EasyList and EasyPrivacy.

![github](image/alg_R.png) [adblock-rust](https://github.com/brave/adblock-rust) - Rust engine for matching network and cosmetic blocking rules.

## 7. Technical Reading & Working Groups

*Where the debates happen and where the reasoning is recorded. Read the issue threads before trusting a summary of any proposal.*

### Working Groups and Specifications

![web](image/alg_I.png) [W3C Privacy Community Group](https://privacycg.github.io/) - Incubates browser-level privacy features such as CHIPS, Storage Access, and Private Click Measurement before standards-track adoption.

![web](image/alg_I.png) [W3C PATCG](https://patcg.github.io/) - Private Advertising Technology Community Group, incubating advertising APIs that carry strong privacy guarantees.

![github](image/alg_R.png) [patcg-individual-drafts](https://github.com/patcg-individual-drafts) - Repository home for individually proposed advertising APIs, including the Topics and Private Aggregation drafts.

![web](image/alg_I.png) [W3C Private Advertising Technology Working Group](https://www.w3.org/2024/11/wg-pat-charter.html) - Charter defining the group’s scope and deliverables for privacy-preserving web advertising APIs.

![web](image/alg_I.png) [W3C Privacy Working Group](https://www.w3.org/groups/wg/privacy/) - Standards-track home of Global Privacy Control and the fingerprinting mitigation guidance.

![web](image/alg_I.png) [IAB Tech Lab Privacy pillar](https://iabtechlab.com/standards/privacy/) - Portfolio view of GPP, TCF, the Data Deletion Request Framework, the Accountability Platform, and the Privacy Taxonomy.

![web](image/alg_I.png) [IAB Tech Lab Addressability & PETs](https://iabtechlab.com/standards/addressability-and-pets/) - Index of PAIR, Curated Audiences, ADMaP, DCR guidance, and the ID and ID-less solution guidance documents.

![web](image/alg_I.png) [Project Rearc](https://iabtechlab.com/project-rearc/) - The multi-year industry effort that produced GPP and Curated Audiences, with the portfolio-approach framing for post-cookie addressability.

![web](image/alg_I.png) [Privacy Principles](https://www.w3.org/TR/privacy-principles/) - W3C statement of data minimisation, purpose limitation, and user-agent responsibilities that any ad-tech specification must be read against.

![web](image/alg_I.png) [Mitigating Browser Fingerprinting](https://www.w3.org/TR/fingerprinting-guidance/) - Taxonomy of fingerprinting surfaces and the mitigation levels expected of specification authors.

![github](image/alg_R.png) [Self-Review Questionnaire: Security and Privacy](https://github.com/w3ctag/security-questionnaire) - The questionnaire W3C specification authors complete, and a practical checklist for pressure-testing a proposed ad API.

![github](image/alg_R.png) [Privacy CG proposals](https://github.com/privacycg/proposals) - Where new browser privacy proposals are argued on the record before they earn a repository.

### Regulatory Guidance

![web](image/alg_I.png) [ICO storage and access technologies guidance](https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-the-use-of-storage-and-access-technologies/about-this-guidance/) - UK regulator guidance on cookies, tracking pixels, fingerprinting, and other device storage and access technologies.

### Engineering Blogs

![web](image/alg_I.png) [WebKit blog](https://webkit.org/blog/) - Primary source for ITP, Web AdAttributionKit, identity-resolution blocking, and Private Browsing changes.

![web](image/alg_I.png) [Privacy Sandbox developer blog](https://privacysandbox.google.com/blog) - Chrome's own announcements, including the deprecation timeline that reshaped the whole stack.

![web](image/alg_I.png) [Brave privacy updates](https://brave.com/privacy-updates/) - Detailed engineering write-ups of fingerprinting, partitioning, and ad-blocking defences.

![web](image/alg_I.png) [Mozilla Privacy & Security](https://blog.mozilla.org/en/privacy-security/) - Firefox's published reasoning on anti-tracking, fingerprint randomisation, and its critique of Protected Audience.

![web](image/alg_I.png) [IAB Tech Lab news](https://iabtechlab.com/iab-tech-lab-news/) - Release notes, finalisations, and public comment windows for every specification listed above.

---

## Contributing

Contributions are welcome. Please read the [contribution guidelines](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md) before submitting a pull request.

## License

[![CC0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors to this repository have waived all copyright and related or neighbouring rights to this work. The full text is in [LICENSE](LICENSE).

This list is released under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) so that it can be reused, remixed, and embedded without attribution friction. Individual projects listed here remain under their own licences — check each repository before adopting code, and note that several entries are specification documents governed by W3C or IAB Tech Lab IPR policies rather than software licences.

[![CC0](https://img.shields.io/badge/CC0-1.0-lightgrey?style=flat-square)](LICENSE)
