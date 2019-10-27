Title: Main News

# Lucene<span style="vertical-align: super; font-size: xx-small">TM</span> Project News

## 6 September 2019 - New mailing lists

The Lucene project has added two new announce mailing lists, `issues@lucene.apache.org` and `builds@lucene.apache.org`.
High-volume automated emails from our bug tracker, JIRA and GitHub will be moved from the `dev@` list to `issues@` and
automated emails from our Jenkins CI build servers will be moved from the `dev@` list to `builds@`.

This is an effort to reduce the sometimes overwhelming email volume on our main development mailing list and thus make it
easier for the community to follow important discussions by humans on the `dev@lucene.apache.org` list.

Everyone who wants to continue receiving these automated emails should sign up for one or both of the two new lists.
Sign-up instructions can be found on the [Lucene-java](https://lucene.apache.org/core/discussion.html)
and [Solr](https://lucene.apache.org/solr/community.html#mailing-lists-irc) web sites.

## 26 July 2019 - Apache Lucene 8.2.0 and Apache Solr 8.2.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 8.2.0 and Apache Solr 8.2.0

Lucene can be downloaded from <https://lucene.apache.org/core/downloads.html> and Solr can be downloaded from <https://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

#### API Changes:

  * Intervals queries has been moved from the sandbox to the queries module.

#### New Features

  * New XYShape Field and Queries for indexing and querying general cartesian geometries.
  * Snowball stemmer/analyzer for the Estonian language.
  * Provide a FeatureSortfield to allow sorting search hits by descending value of a feature.
  * Add new KoreanNumberFilter that can change Hangul character to number and process decimal point.
  * Add doc-value support to range fields.
  * Add monitor subproject (previously Luwak monitoring library) that allows a stream of documents to be matched against a set of registered queriesin an efficient manner.
  * Add a numeric range query in sandbox that takes advantage of index sorting.Add a numeric range query in sandbox that takes advantage of index sorting.

#### Optimizations

  * Use exponential search instead of binary search in IntArrayDocIdSet#advance method.
  * Use incoming thread for execution if IndexSearcher has an executor. Now caller threads execute at least one search on an index even if there is an executor provided to minimize thread context switching.
  * New storing strategy for BKD tree leaves with low cardinality that can lower storage costs and It can be used at search time to speed up queries.
  * Load frequencies lazily only when needed in BlockDocsEnum and BlockImpactsEverythingEnum.
  * Phrase queries now leverage impacts.

### Highlights of this Solr release include:

#### New features

  * Add an update param failOnVersionConflicts=false to updates not fail when there is a version conflict
  * Add facet2D Streaming Expression.
  * Preferred replicas on nodes with same system properties as the query master
  * OpenTracing support for Solr
  * Raw index data analysis tool (extension of COLSTATUS collection command).
  * Add recNum Stream Evaluator.
  * Allow zplot to visualize 2D clusters and convex hulls.
  * Add a field type for Estonian language to default managed_schema, document about Estonian language analysis in Solr Ref Guide

#### Bug Fixes

  * Intermittent 401's for internode requests with basicauth enabled.
  * In 8.1, Atomic Updates were broken (NPE) when the schema declared the new _nest_path_ field even if you weren't using nested docs. In-place updates were not affected (worked)
  * Fix atomic update encoding issue for UUID, enum, bool, and binary fields.
  * Impossible to delete a collection with the same name as an existing alias. This fixes also a bug inREINDEXCOLLECTION when used with removeSource=true which could lead to a data loss.

## 4 June 2019, Apache Lucene 7.7.2 and Apache Solr 7.7.2 available

The Lucene PMC is pleased to announce the release of Apache® Lucene™ 7.7.2 and Apache® Solr™ 7.7.2.

Lucene can be downloaded from <https://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <https://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

  * This release contains 9 bugfixes in Lucene

### Highlights of this Solr release include:

  * High CPU usage in Solr due to Java 8 bug (SOLR–13349)
  * Multiplicative query boost in certain conditions not applied (SOLR–13126)
  * InPlace update sometimes fail if schema has a required field (SOLR–11876)
  * Admin UI inaccessible with RuleBasedAuthorizationPlugin (SOLR–13344)
  * MetricsHistoryHandler does not work with BasicAuth (SOLR–12860)
  * ByteArrayUtf8CharSequence cannot be cast to java.lang.String (SOLR–13285)

## 28 May 2019 - Apache Lucene 8.1.1 and Apache Solr 8.1.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 8.1.1 and Apache Solr 8.1.1

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Solr release include:

  * Fix for a Null Pointer Exception when querying collection through collection alias.

## 16 May 2019 - Apache Lucene 8.1.0 and Apache Solr 8.1.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 8.1.0 and Apache Solr 8.1.0

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

  * A query introspection API has been introduced.
  * Luke, well-known GUI for inspecting Lucene indexes, now added as a Lucene module
  * Merging dimensional points to use radix partitioning, which has also been optimized
  * Bugfix: LatLonShapePolygonQuery returns incorrect WITHIN results with shared boundaries
  * TieredMergePolicy#findForcedMerges now tries to create the cheapest merges
  * Build point writers in the BKD tree only when they are needed
  * SynonymQuery can now deboost the document frequency of each term when blending synonym scores
  * ConstantScoreQuery can early terminate if minimum score > constant score (total hits are not requested)
  * DateRangePrefixTree can now parse more precise dates

### Highlights of this Solr release include:

  * Partial/Atomic Updates for nested documents. This enables atomic updates for nested documents, without the need to supply the whole nested hierarchy (which would be overwritten if absent).
  * Category Routed Aliases feature introduced for data driven assignment of documents to collections based on values of a field
  * JWT Token authentication plugin with OpenID Connect implicit flow login through Admin UI
  * REINDEXCOLLECTION command for re-indexing of existing collections
  * Collection RENAME command and support using aliases in most collection admin commands
  * Read-only mode for SolrCloud collections
  * Handling of incorrect or absent values was improved for many request parameters. In such cases the response is 400 http code (Bad Request), instead of 500 (Internal Server Error) as it was before.
  * Breaching timeAllowed limit correctly responded as 200 http code (Ok) with partialResults=true, instead of 500 (Internal Server Error) as it was before in SolrCloud. Note, it was fixed for essential request parameters, if you still evidence 500 caused by timeAllowed, please submit an issue with log excerpt attached.
  * In-place updates work for collections created with route.field.
  * Asynchronous Collection API calls do not return completion status prematurely when more than one replica reside per note.
  * Range Facets and Terms Component performance has been optimized for certain cases.

## 5 April 2019 - Apache Lucene 6.6.6 and Apache Solr 6.6.6 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.6 and Apache Solr 6.6.6

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.6>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.6>

### Highlights of this Solr release include:

 * Fix memory leak (upon collection reload or ZooKeeper session expiry) in ZkIndexSchemaReader.
 * Fix for Rule-based Authorization skipping authorization if querying node host the collection
 * (CVE-2017-3164) Make it possible to configure a host whitelist for distributed search

## 14 March 2019 - Apache Lucene 8.0.0 and Apache Solr 8.0.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 8.0.0 and Apache Solr 8.0.0

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

#### Query execution

Term queries, phrase queries and boolean queries introduced new optimization that enables efficient skipping over non-competitive documents when the total hit count is not needed. Depending on the exact query and data distribution, queries might run between a few percents slower and many times faster, especially term queries and pure disjunctions.

In order to support this enhancement, some API changes have been made:
 * `TopDocs.totalHits` is no longer a long but an object that gives a lower bound of the actual hit count.
 * `IndexSearcher`'s `search` and `searchAfter` methods now only compute total hit counts accurately up to 1,000 in order to enable this optimization by default.
 * Queries are now required to produce non-negative scores.

#### Codecs

 * Postings now index score impacts alongside skip data. This is how term queries optimize collection of top hits when hit counts are not needed.
 * Doc values introduced jump tables, so that advancing runs in constant time. This is especially helpful on sparse fields.
 * The terms index `FST` is now loaded off-heap for non-primary-key fields using `MMapDirectory`, reducing heap usage for such fields.

#### Custom scoring

The new `FeatureField` allows efficient integration of static features such as a pagerank into the score. Furthermore, the new `LongPoint#newDistanceFeatureQuery` and `LatLonPoint#newDistanceFeatureQuery` methods allow boosting by recency and geo-distance respectively. These new helpers are optimized for the case when total hit counts are not needed. For instance if the pagerank has a significant weight in your scores, then Lucene might be able to skip over documents that have a low pagerank value.

### Highlights of this Solr release include:

* Solr now uses HTTP/2 for inter-node communication

Being a major release, Solr 8 removes many deprecated APIs, changes various parameter defaults and behavior. Some changes may require a re-index of your content.
You are thus encouraged to thoroughly read the "Upgrade Notes" at:

  <http://lucene.apache.org/solr/8_0_0/changes/Changes.html>

Solr 8.0 also includes many other new features as well as numerous optimizations and bugfixes of the corresponding Apache Lucene release.

## 1 March 2019 - Apache Lucene 7.7.1 and Apache Solr 7.7.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.7.1 and Apache Solr 7.7.1

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

This Lucene release contains no change over Lucene 7.7.0.

### Highlights of this Solr release include:

 * Bugfix for ClassCastException when URPs try to read a String field which returns a ByteArrayUTF8CHarSequence (a
   regression in release 7.7.0).

 * Bugfix: Autoscaling based replica placement was broken out of the box. Solr 7.5 enabled autoscaling based replica
   placement by default but in the absence of default cluster policies, autoscaling can place more than 1 replica of the
   same shard on the same node. Also, the maxShardsPerNode and createNodeSet was not respected. Due to these reasons,
   this issue reverts the default replica placement policy to the 'legacy' assignment policy that was the default until
   Solr 7.4.


## 11 February 2019 - Apache Lucene 7.7.0 and Apache Solr 7.7.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.7.0 and Apache Solr 7.7.0

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

#### Bug Fixes

  * Fix LatLonShape WITHIN queries that fail with Multiple search Polygons that share the dateline.
  * LatLonShape's within and disjoint queries can return false positives with indexed multi-shapes.

#### Improvements

  * ExitableDirectoryReader may now time out queries that run on points such as range queries or geo queries.
  * StandardTokenizer and UAX29URLEmailTokenizer now support Unicode 9.0, and provide Unicode UTS#51 v11.0 Emoji tokenization with the "<EMOJI>" token type.
  * TopFieldCollector can now early-terminates queries when sorting by SortField.DOC.
  * Speed up merging segments of points with data dimensions by only sorting on the indexed dimensions.
  * The KoreanTokenizer no longer splits unknown words on combining diacritics and detects script boundaries more accurately with Character#UnicodeScript#of.
  * Change LatLonShape encoding to use 4 bytes Per Dimension.
  * BufferedUpdates now uses an optimized storage for buffering docvalues updates that can save up to 80% of the heap used compared to the previous implementation and uses non-object based datastructures.
  * Moved to the default accepted overhead ratio for packet ints in DocValuesFieldUpdates yields an up-to 4x performance improvement when applying doc values updates.
  * Doc-value updates get applied faster by sorting with quicksort, rather than an in-place mergesort, which needs to perform fewer swaps.
  * Decrease I/O pressure when merging high dimensional points.

### Highlights of this Solr release include:

  * URI Too Long with large streaming expressions in SolrJ.
  * A failure while reloading a SolrCore can result in the SolrCore not being closed.
  * Spellcheck parameters not working in new UI.
  * New Admin UI Query does not URL-encode the query produced in the URL box.
  * Rule-base Authorization plugin skips authorization if querying node does not have collection replica.
  * Solr installer fails on SuSE linux.
  * Fix incorrect SOLR_SSL_KEYSTORE_TYPE variable in solr start script.
  * JSON 'terms' Faceting now supports a 'prelim_sort' option to use when initially selecting the top ranking buckets, prior to the final 'sort' option used after refinement.
  * Add a login page to Admin UI, with initial support for Basic Auth and Kerberos.
  * New Node-level health check handler at /admin/info/healthcheck and /node/health paths that checks if the node is live, connected to zookeeper and not shutdown.
  * It is now possible to configure a host whitelist for distributed search.

## 14 December 2018 - Apache Lucene 7.6.0 and Apache Solr 7.6.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.6.0 and Apache Solr 7.6.0

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

#### Bug Fixes

  * Index sorting corruption due to numeric overflow has been fixed. Indices affected by this bug can be detected by running the CheckIndex command on a 7.6+ release distribution.
  * Better tessellation processing of Polygons including graceful exceptions for detecting invalid shapes.

#### Improvements

  * Points codec now supports `selective indexing`; the ability to designate dimensions as as "data only" dimensions that do not affect construction of the index.
  * New Simple WKT Shape Parser builds lucene geometries (polygons, lines, rectangles) from WKT format.
  * New LatLonShapeLineQuery queries indexed shapes with arbitrary lines.
  * Performance in PerFieldMergeState#FilterFieldInfos has been improved from O(N) to O(1) lookup time.

### Highlights of this Solr release include:

  * Field and FieldType now support a new `uninvertible` option to control using costly field cache or more efficient docValues.
  * Collections API has been improved to support adding multiple replicas to a collection shard at a time as well as splitting into multiple sub-shards directly..
  * Autoscaling's suggestions API now include rebalance options as well as suggestions to add new replicas for lost replicas.
  * Several new Stream Evaluators have been added to include: oscillate, convexHull, enclosingDisk, pairSort, log10, percentiles, and pivot for geometric and scientific analysis.
  * UnifiedHighlighter has been improved to support best/perfect highlighting accuracy and full phrase highlighting.

## 24 September 2018- Apache Lucene 7.5.0 and Apache Solr 7.5.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.5.0 and Apache Solr 7.5.0

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.5.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.5.0>

### Highlights of this Lucene release include:

#### Bug Fixes

  * IndexWriter#deleteDocs(Query... query) applies deletes to wrong documents if the index is sorted.

#### Changes in Runtime behavior

  * TieredMergePolicy now respects maxSegmentSizeMB by default when executing findForcedMerges and findForcedDeletesMerges.

#### Improvements

  * A new points based Shape Indexing and Searching that decomposes shapes into a triangular mesh and indexes individual triangles as a 6 dimension point.
  * A new ByteBuffer based Directory implementation that aims to replace the deprecated RAMDirectory.
  * The UnifiedHighlighter can now use the MatchesIterator API to highlight any query more accurately.
  * TopFieldComparator can now stop comparing documents if the index is sorted, even if hits still need to be visited to compute the hit count.
  * TieredMergePolicy can control how aggressively deletes should be reclaimed with the new deletesPctAllowed setting.

### Highlights of this Solr release include:

  * Nested/child documents may now be supplied as a field value instead of stand-off. Future releases will leverage this semantic information.
  * Enhance Autoscaling policy support to equally distribute replicas on the basis of arbitrary properties.
  * Nodes are now visible inside a view of the Admin UI "Cloud" tab, listing nodes and key metrics.
  * The status of zookeeper ensemble is now accessible under the Admin UI Cloud tab.
  * The new Korean morphological analyzer ("nori") has been added to default distribution.

## 3 July 2018 - Apache Lucene 6.6.5 and Apache Solr 6.6.5 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.5 and Apache Solr 6.6.5

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.5>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.5>

### Highlights of this Solr release include:

 * Ability to disable configset upload via -Dconfigset.upload.enabled=false startup parameter
 * Referal to external resources in various config files now disallowed

## 27 June 2018 - Apache Lucene 7.4.0 and Apache Solr 7.4.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.4.0 and Apache Solr 7.4.0

Lucene can be downloaded from <http://lucene.apache.org/core/downloads.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/downloads.html>

### Highlights of this Lucene release include:

#### Analysis

 * Korean analyzer
 * Support emoji sequence tokens with ICUTokenizer

#### Queries

 * The new IntervalQuery implements proximity search based on minimum-interval semantics
 * Queries may now iterate over positions and matches on a given document thanks to the Weight#matches API

#### Indexing

 * New soft-delete mechanism with a configurable retention policy
 * Doc-value updates may reset a value
 * Doc-values may be atomically updated with a regular document update

### Highlights of this Solr release include:

 * A new 'relatedness()' aggregate function for JSON Faceting to enable building Semantic Knowledge Graphs.
 * Added the TaggerRequestHandler (AKA SolrTextTagger) for tagging text. It's used as a component of NER/ERD systems including query-understanding.
 * The "Auto Scaling" feature area has been added to and enhanced a lot.
 * The "Streaming Expressions" feature area has been added to and enhanced a lot.
 * Upgraded from Log4j 1.x to 2.x.  Solr continues to log via SLF4J.

## 18 May 2018 - Apache Lucene 6.6.4 and Apache Solr 6.6.4 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.4 and Apache Solr 6.6.4

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.4>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.4>

### Highlights of this Solr release include:

 * Do not allow to use absolute URIs for including other files in solrconfig.xml and schema parsing

## 15 May 2018 - Apache Lucene 7.3.1 and Apache Solr 7.3.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.3.1 and Apache Solr 7.3.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.3.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.3.1>

### Highlights of this Lucene release include:

 * This release contains one build change

### Highlights of this Solr release include:

 * Deleting replicas sometimes fails and causes the replicas to exist in the down state
 * Upgrade commons-fileupload dependency to 1.3.3 to address CVE-2016-1000031
 * Do not allow to use absolute URIs for including other files in solrconfig.xml and schema parsing
 * A successful restore collection should mark the shard state as active and not buffering

## 4 April 2018 - Apache Lucene 7.3.0 and Apache Solr 7.3.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.3.0 and Apache Solr 7.3.0

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.3.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.3.0>

### Highlights of this Lucene release include:

 * An OpenNLP analysis module
 * IndexWriter can opt out of flushing on indexing threads
 * Shapes can be indexed using Google S2 geometry
 * Better relevancy for highlighted passages containing phrases
 * Java 9 performance improvements

### Highlights of this Solr release include:

 * OpenNLP request processors
 * Automatic time-based collection creation
 * Multivalued primitive fields can be used in sorting
 * SortableTextField allows sorting and faceting on free text
 * New stream evaluators
 * Improvements around leader-initiated recovery
 * New autoscaling features
 * A Prometheus metrics exporter
 * Filtering with exclusions on parent and child queries
 * Filtering with exclusions via a new query parser
 * Neural network modelling via learning to rank
 * Solr runs with Java 10

## 7 March 2018 - Apache Lucene 6.6.3 and Apache Solr 6.6.3 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.3 and Apache Solr 6.6.3.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.3>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.3>

### Highlights of this Lucene release include:

 * This release contains one build change

### Highlights of this Solr release include:

 * Disallow reference to external resources in DataImportHandler's dataConfig request parameter
 * Allow collections created with legacyCloud=true to be opened if legacyCloud=false
 * LeaderInitiatedRecoveryThread now retries on UnknownHostException

## 15 January 2018 - Apache Lucene 7.2.1 and Apache Solr 7.2.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.2.1 and Apache Solr 7.2.1.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.2.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.2.1>

### Highlights of this Lucene release include:

 * Fix advanceExact on SortedNumericDocValues produced by Lucene54DocValuesProducer.

### Highlights of this Solr release include:

 * Overseer can never process some last messages.
 * Rename core in solr standalone mode is not persisted.
 * QueryComponent's rq parameter parsing no longer considers the defType parameter.
 * Fix NPE in SolrQueryParser when the query terms inside a filter clause reduce to nothing.

## 21 December 2017 - Apache Lucene 7.2.0 and Apache Solr 7.2.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.2.0 and Apache Solr 7.2.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.2.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.2.0>

### Highlights of this Lucene release include:

 * Specific query implementations can now opt out of caching.
 * TopFieldDocCollector can now early terminate collection of matches when the index is sorted and the total hit count is not requested.
 * IndexWriter#flushNextBuffer gives more fine-grained control over the memory usage of IndexWriter.
 * Fixed document accounting in IndexWriter.
 * Query scores can be exposed in a ValuesSource using DoubleValuesSource.fromQuery().

### Highlights of this Solr release include:

 * Bi-directional syncing of CDCR clusters is now supported.
 * The new synonymQueryStyle field type option allows for better scoring when terms at the same position are hyponyms/hypernyms rather than synonyms.
 * More stream evaluators, including: matrix operations; spline; derivative; regression; normalization; scaling; correlation; markov chains; time series differencing; and triangular and geometric distributions.
 * The new facet.matches parameter returns facet buckets only for terms that match a regular expression.
 * New Autoscaling features: the autoscaling/suggestions API end-point; the UTILIZENODE command, which moves replicas according to autoscaling policies and preferences; and the Autoscaling set-property command.

## 24 October 2017, Apache Lucene 5.5.5 and Apache Solr 5.5.5 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.5 and Apache Solr 5.5.5.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.5> and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.5>

### This Lucene release includes a critical security fix:

 * Disallow resolving of external entities in queryparser/xml/CoreParser by default.

### This Solr release includes one critical and one important security fix. Details:

 * Fix for a 0-day exploit (CVE-2017-12629), details: <https://s.apache.org/FJDl>. RunExecutableListener has been disabled by default (can be enabled by -Dsolr.enableRunExecutableListener=true) and resolving external entities in the XML query parser (defType=xmlparser or {!xmlparser ... }) is disabled by default.

 * Fix for CVE-2017-7660: Security Vulnerability in secure inter-node communication in Apache Solr, details: <https://s.apache.org/APTY>

## 18 October 2017, Apache Lucene 6.6.2 and Apache Solr 6.6.2 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.2 and Apache Solr 6.6.2.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.2>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.2>

### Highlight of this Lucene release includes:

Critical security fix:

 * Disallow resolving of external entities in queryparser/xml/CoreParser by default.

### Highlights of this Solr release include:

 * Critical security fix: Fix for a 0-day exploit (CVE-2017-12629), details: https://s.apache.org/FJDl. RunExecutableListener has been disabled by default (can be enabled by -Dsolr.enableRunExecutableListener=true) and resolving external entities in the XML query parser (defType=xmlparser or {!xmlparser ... }) is disabled by default.

 * Fix a bug where Solr was attempting to load the same core twice (Error message: "Lock held by this virtual machine").

## 17 October 2017 - Apache Lucene 7.1.0 and Apache Solr 7.1.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.1.0 and Apache Solr 7.1.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.1.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.1.0>

### Highlights of this Lucene release include:

 * New Geo3D shapes for non-spherical planet models

 * Serialization and deserialization support for Geo3D

 * A new CoveringQuery, whose required number of matching clauses can be defined per document

 * New BengaliAnalyzer for Bengali language

 * A point based range field called LatLonBoundingBox

 * FloatPointNearestNeighbor, an N-dimensional FloatPoint K-nearest-neighbor search implementation

 * Faster default taxonomy cache

 * Support for computing facet counts for individual numeric values via LongValueFacetCounts

 * Faster geo-distance queries in case of dense single-valued fields when most documents match

 * Better heuristics in IndexOrDocValuesQuery

 * Optimized builds for OrdinalMap (used by SortedSetDocValuesFacetCounts and others)

### Highlights for this Solr release include:

 * Critical Security Update: Fix for CVE-2017-12629 which is a working 0-day exploit reported on the [public mailing list](https://s.apache.org/FJDl).

 * Auto-scaling: Solr can now move replicas automatically when a new node is added or an existing node is removed using the auto scaling policy framework introduced in 7.0

 * Auto-scaling: The 'autoAddReplicas' feature which was limited to shared file systems is now available for all file systems. It has been ported to use the new autoscaling framework internally.

 * Auto-scaling: New set-trigger, remove-trigger, set-listener, remove-listener, suspend-trigger, resume-trigger APIs

 * Auto-scaling: New /autoscaling/history API to show past autoscaling actions and cluster events

 * New JSON based Query DSL for Solr that extends JSON Request API to also support all query parsers and their nested parameters

 * JSON Facet API: min/max aggregations are now supported on single-valued date fields

 * Lucene's Geo3D (surface of sphere & ellipsoid) is now supported on spatial RPT fields by setting spatialContextFactory="Geo3D". Furthermore, this is the first time Solr has out of the box support for polygons

 * Expanded support for statistical stream evaluators such as various distributions, rank correlations, distances and more.

 * Multiple other optimizations and bug fixes

See the [Lucene CHANGES.txt](/core/7_1_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/7_1_0/changes/Changes.html) files included
with the release for a full list of details.

## 12 October 2017 - Please secure your Apache Solr servers since a zero-day exploit has been reported on a public mailing list

Please secure your Solr servers since a zero-day exploit has been
reported on a [public mailing list](https://s.apache.org/FJDl).
This has been assigned a public CVE (CVE-2017-12629) which we
will reference in future communication about resolution and mitigation
steps.

Here is what we're recommending and what we're doing now:

* Until fixes are available, all Solr users are advised to restart their
Solr instances with the system parameter `-Ddisable.configEdit=true`.
This will disallow any changes to be made to configurations via the
Config API. This is a key factor in this vulnerability, since it allows
GET requests to add the RunExecutableListener to the config. This is
sufficient to protect you from this type of attack, but means you cannot
use the edit capabilities of the Config API until the other fixes
described below are in place. Users are also advised to remap
the XML Query Parser to another parser to mitigate the XXE
vulnerability. For example, adding the following to the solrconfig.xml
file maps the `xmlparser` to the `edismax` parser:
`<queryParser name="xmlparser" class="solr.ExtendedDismaxQParserPlugin"/>`.

* A new release of Lucene/Solr was in the vote phase, but we have now
pulled it back to be able to address these issues in the upcoming 7.1
release. We will also determine mitigation steps for users on earlier
versions, which may include a 6.6.2 release for users still on 6.x.

* The RunExecutableListener will be removed in 7.1. It was previously
used by Solr for index replication but has been replaced and is no
longer needed.

* The XML Parser will be fixed and the fixes will be included in the 7.1
release.

* The 7.1 release was already slated to include a change to disable the
`stream.body` parameter by default, which will further help protect
systems.

## 6 October 2017 - Apache Lucene 7.0.1 and Apache Solr 7.0.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.0.1 and Apache Solr 7.0.1.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.0.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.0.1>

### The Lucene release includes 1 bug fix since the 7.0.0 release:

 * ConjunctionScorer.getChildren was failing to return all child scorers

### The Solr release includes 2 bug fixes since the 7.0.0 release:

 * Solr 7.0 cannot read indexes from 6.x versions.

 * Message "Lock held by this virtual machine" during startup.  Solr is trying to start some cores twice.

See the [Lucene CHANGES.txt](/core/7_0_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/7_0_1/changes/Changes.html) files included
with the release for a full list of details.

## 20 September 2017 - Apache Lucene 7.0.0 and Apache Solr 7.0.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 7.0.0 and Apache Solr 7.0.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/7.0.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/7.0.0>

### Highlights of this Lucene release include:

 * Doc values switched from random access to iterators.

 * The 7.0 codec now sparsely encodes sparse doc values and length normalization factors ("norms"), which also translates to optimization in both indexing, and search on sparse values. With these changes, you finally only pay for what you actually use with doc values, in index size, indexing performance, etc.

 * Index time boost for documents is now removed.

 * Substantial performance gains for delete and update heavy Lucene usage; see http://blog.mikemccandless.com/2017/07/lucene-gets-concurrent-deletes-and.html for details

 * Query scoring is now simpler with removal of coord factor, and query normalization.

 * Classic query parser no longer splits on whitespaces. This enables better multi-word synonym support.

 * The version of Lucene that created the index segment would be recorded, along with the version that last modified the index.

 * IndexWriter, used to add, update and delete documents in your index, will no longer accept broken token offsets sometimes produced by mis-behaving token filters.

 * IndexReader exposes methods that are typically used to manage resources whose lifetime needs to mimic the lifetime of segments/indexes, typically caches. They have been made much less trappy.

 * The dimensional points API now takes a field name up front to offer per-field points access, matching how the doc values APIs work.

 * The PostingsHighlighter was removed. Migrating to the UnifiedHighlighter should be straight-forward.

### Highlights for this Solr release include:

 * Replica Types - Solr 7 supports different replica types, which handle updates differently. In addition to pure NRT operation where all replicas build an index and keep a replication log, you can now also add so called PULL replicas, achieving the read-speed optimized benefits of a master/slave setup while at the same time keeping index redundancy.

 * Auto-scaling. Solr can now allocate new replicas to nodes using a new auto scaling policy framework. This framework will in future releases enable Solr to move shards around based on load, disk etc.

 * Indented JSON is now the default response format for all APIs, pass wt=xml and/or indent=off to use the previous unindented XML format.

 * The JSON Facet API now supports two-phase facet refinement to ensure accurate counts and statistics for facet buckets returned in distributed mode.

 * Streaming Expressions adds a new statistical programming syntax for the statistical analysis of sql queries, random samples, time series and graph result sets.

 * Analytics Component version 2.0, which now supports distributed collections, expressions over multivalued fields, a new JSON request language, and more.

 * The new v2 API, exposed at /api/ and also supported via SolrJ, is now the preferred API, but /solr/ continues to work.

 * A new '_default' configset is used if no config is specified at collection creation. The data-driven functionality of this configset indexes strings as analyzed text while at the same time copying to a '*_str' field suitable for faceting.

Both Apache Lucene and Solr 7.0.0 were tested to be fully compatible with the release of Java 9 and its module system Jigsaw, coming out tomorrow on September 21st!

See the [Lucene CHANGES.txt](/core/7_0_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/7_0_0/changes/Changes.html) files included
with the release for a full list of details.

## 7 September 2017 - Apache Lucene 6.6.1 and Apache Solr 6.6.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.1 and Apache Solr 6.6.1.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.1>

### Highlights of this Lucene release include:

  * Documents with multiple points that should match might not match on a memory index

  * A query which has only one synonym with AND as the default operator would wrongly translate as an AND between the query term and the synonym

### Highlights of this Solr release include:

  * Standalone Solr loads UNLOADed core on request

  * ParallelStream should set the StreamContext when constructing SolrStreams

  * CloudSolrStream.toExpression incorrectly handles fq clauses

  * CoreContainer.load needs to send lazily loaded core descriptors to the proper list rather than send them all to the transient lists

  * Creating a core should write a core.properties file first and clean up on failure

  * Clean up a few details left over from pluggable transient core and untangling

  * Provide a way to know when Core Discovery is finished and when all async cores are done loading

  * CDCR bootstrapping can get into an infinite loop when a core is reloaded

  * SolrJmxReporter is broken on core reload. This resulted in some or most metrics not being reported via JMX after core reloads, depending on timing

  * Creating a core.properties fails if the parent of core.properties is a symlinked directory

  * StreamHandler should allow connections to be closed early

  * Certain admin UI pages would not load up correctly with kerberos enabled

  * Fix DOWNNODE -> queue-work znode explosion in ZooKeeper

  * Upgrade to Hadoop 2.7.4 to fix incompatibility with Java 9

  * Fix bin/solr.cmd so it can run properly on Java 9

See the [Lucene CHANGES.txt](/core/6_6_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_6_1/changes/Changes.html) files included
with the release for a full list of details.

## 6 June 2017 - Apache Lucene 6.6.0 and Apache Solr 6.6.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.6.0 and Apache Solr 6.6.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.6.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.6.0>

### Highlights of this Lucene release include:

  * A concurrent SortedSet facets implementation

  * spatial-extras HeatmapFacetCounter will now short-circuit it's work when Bits.MatchNoBits is passed

  * OfflineSorter now passes the total number of items it will write to getWriter()

  * Move dictionary for Ukrainian analyzer to external dependency

  * SortedSetDocValuesReaderState now implements Accountable so one can see how much RAM it is using

  * OfflineSorter can now run concurrently if you pass it an optional ExecutorService Sorted set facets now use sparse storage when collecting hits, when appropriate

  * PostingsHighlighter has been deprecated in favour of the UnifiedHighlighter

### Highlights of this Solr release include:

  * Payload support with payload() value source and {!payload_score} and {!payload_check} query parsers

  * Solr support for SimpleTextCodec

  * Multi-field support to TermsComponent when requesting terms' statistics

  * New AtomicUpdateProcessor to convert normal update operations to atomic update operations

  * UPLOAD command (Config Set API) for uploading zipped configsets

  * MOVEREPLICA command (Collections API) for moving a replica across nodes

  * LISTALIASES command (Collections API) to return a list of all collection aliases

  * STATUS command (Core Admin API) to emit collection details of each core

  * Basic authentication can be enabled/disabled using bin/solr|bin/solr.cmd

  * Solr default/example uses WordDelimiterGraphFilterFactory and SynonymGraphFilterFactory

  * Expose cache statistics using metrics API

  * CloudSolrClient can now be initialized using the base URL of a Solr instance instead of ZooKeeper hosts

  * Grouping, CollapseQParser and ExpandComponent support with PointFields

  * Variance and Standard Deviation aggregators for the JSON Facet API

  * JSON Faceting now supports a query time 'join' domain change option

  * CartesianProductStream, which turns a single tuple with a multi-valued field into N tuples, one for each value in the multi-valued field

  * New Streaming Evaluators: Basic math, UUID, Date/time, correlation, regress, predict, covariance, convolution, normalize

  * New Streaming Expressions: shuffle, echo, eval, timeseries, let, get, tuple

See the [Lucene CHANGES.txt](/core/6_6_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_6_0/changes/Changes.html) files included
with the release for a full list of details.

## 27 April 2017 - Apache Lucene 6.5.1 and Apache Solr 6.5.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.5.1 and Apache Solr 6.5.1.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.5.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.5.1>

### Highlights of this Lucene release include:

  * Fixed join queries to not reference IndexReaders, as it could cause leaks if they are cached.

  * Made LRUQueryCache delegate the scoreSupplier method.

  * Fixed index sorting to work with sparse numeric and binary docvalues field

### Highlights of this Solr release include:

  * bin\solr.cmd delete and healthcheck now works again; fixed continuation chars ^

  * Fix debug related NullPointerException in solr/contrib/ltr OriginalScoreFeature class.

  * The JSON output of /admin/metrics is fixed to write the container as a map (SimpleOrderedMap) instead of an array (NamedList).

  * On 'downnode', lots of wasteful mutations are done to ZK.

  * Fix params persistence for solr/contrib/ltr (MinMax|Standard)Normalizer classes.

  * The fetch() streaming expression wouldn't work if a value included query syntax chars (like :+-). Fixed, and enhanced the generated query to not pollute the queryCache.

  * Disable graph query production via schema configuration <fieldtype ... enableGraphQueries="false">. This fixes broken queries for ShingleFilter-containing query-time analyzers when request param sow=false.

  * Fix indexed="false" on numeric PointFields

  * SQL AVG function mis-interprets field type.

  * SQL interface does not use client cache.

  * edismax with sow=false fails to create dismax-per-term queries when any field is boosted.

See the [Lucene CHANGES.txt](/core/6_5_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_5_1/changes/Changes.html) files included
with the release for a full list of details.

## 27 March 2017 - Apache Lucene 6.5.0 and Apache Solr 6.5.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.5.0 and Apache Solr 6.5.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.5.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.5.0>

### Highlights of this Lucene release include:

 * It is now possible filter out duplicates in the NRT suggester

 * SimpleQueryString now supports default fuziness

 * IndexWriter can return the list of visible field names

 * DisjunctionScorer now supports returning the matching children clauses

 * A new FunctionScoreQuery that modifies the internal query's score using the per-document values

 * A new FunctionMatchQuery that returns any documents with a value that matches a predicate

 * A new WordDelimiterGraphFilter that outputs a correct graph structure for multi-token expansion at query time

 * A new PatternTokenizer that uses Lucene's RegExp implementation

 * RangeFieldQuery now supports CROSSES relation

 * A new IndexOrDocValuesQuery that uses either an index (points or terms) or doc values in order to run a (range, geo box and distance) query, depending which one is more efficient

 * index-time boosts are deprecated

 * Term filters are no longer cached

 * Compound filters are cached earlier than regular queries

 * BKDReader now calls grow on larger increments

 * LatLonPointInPolygonQuery are faster

 * LatLonPointDistanceQuery now skips distance computations more often

 * To-parent block joins now implements two-phase iteration

 * Point ranges that match most documents are faster

 * PointValues#estimatePointCount is faster with Relation.CELL_INSIDE_QUERY

 * Segments are now also sorted during flush, and merging on a sorted index is substantially faster by using some of the same bulk merge optimizations that non-sorted merging uses

### Highlights of this Solr release include:

 * PointFields (fixed-width multi-dimensional numeric & binary types enabling fast range search) are now supported

 * In-place updates to numeric docValues fields (single valued, non-stored, non-indexed) supported using atomic update syntax

 * A new LatLonPointSpatialField that uses points or doc values for query

 * It is now possible to declare a field as "large" in order to bypass the document cache

 * New sow=false request param (split-on-whitespace) for edismax & standard query parsers enables query-time multi-term synonyms

 * XML QueryParser (defType=xmlparser) now supports span queries

 * hl.maxAnalyzedChars now have consistent default across highlighters

 * UnifiedSolrHighlighter and PostingsSolrHighlighter now support CustomSeparatorBreakIterator

 * Scoring formula is adjusted for the scoreNodes function

 * Calcite Planner now applies constant Reduction Rules to optimize plans

 * A new significantTerms Streaming Expression that is able to extract the significant terms in an index

 * StreamHandler is now able to use runtimeLib jars

 * Arithmetic operations are added to the SelectStream

 * Added modernized self-documenting /v2 API

 * The .system collection is now created on first request if it does not exist

 * Admin UI: Added shard deletion button

 * Metrics API now supports non-numeric metrics (version, disk type, component state, system properties...)

 * The disk free and aggregated disk free metrics are now reported

 * The DirectUpdateHandler2 now implements MetricsProducer and exposes stats via the metrics api and configured reporters.

 * BlockCache is faster due to less failures when caching a new block

 * MMapDirectoryFactory now supports "preload" option to ask mapped pages to be loaded into physical memory on init

 * Security: BasicAuthPlugin now supports standalone mode

 * Arbitrary java system properties can be passed to zkcli

 * SolrHttpClientBuilder can be configured via java system property

 * Javadocs and Changes.html are no longer included in the binary distribution, but are hosted online

See the [Lucene CHANGES.txt](/core/6_5_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_5_0/changes/Changes.html) files included
with the release for a full list of details.

## 7 March 2017 - Apache Lucene 6.4.2 and Apache Solr 6.4.2 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.4.2 and Apache Solr 6.4.2.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.4.2>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.4.2>

### Highlights of this Lucene release include:

  * Fixed: CommonGramsQueryFilter was producing a disconnected token graph, messing up phrase queries during query parsing

### Highlights of this Solr release include:

  * Fixed: Serious performance degradation in Solr 6.4 due to the metrics collection. IndexWriter metrics collection turned off by default, directory level metrics collection completely removed (until a better design is found)

  * Fixed: Transaction log replay can hit an NullPointerException due to new Metrics code

  * Fixed: NullPointerException in CloudSolrClient when reading stale alias

  * Fixed: UnifiedHighlighter and PostingsHighlighter bug in PrefixQuery and TermRangeQuery for multi-byte text

See the [Lucene CHANGES.txt](/core/6_4_2/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_4_2/changes/Changes.html) files included
with the release for a full list of details.

## 15 February 2017 - Apache Lucene 5.5.4 and Apache Solr 5.5.4 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.4 and Apache Solr 5.5.4.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.4>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.4>

### Highlights of this Lucene release include:

 * Made stored fields reclaim native memory more aggressively

 * Fixed a potential memory leak with LRUQueryCache and (Span)TermQuery

 * MmapDirectory's unmapping code is now compatible with Java 9 (EA build 150 and later)

### Highlights of this Solr release include:

 * Better validation of filename params in ReplicationHandler

 * Upgraded commons-fileupload to 1.3.2, fixing a potential vulnerability CVE-2016-3092

See the [Lucene CHANGES.txt](/core/5_5_4/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_5_4/changes/Changes.html) files included
with the release for a full list of details.


## 6 February 2017 - Apache Lucene 6.4.1 and Apache Solr 6.4.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.4.1 and Apache Solr 6.4.1.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.4.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.4.1>

### Highlights of this Lucene release include:

  * Javadocs now build successfully with Java 8u121

  * Fixed memory leak in the case that TermQuery or SpanTermQuery objects that wrap a TermContext were cached

  * Fixed native memory leak when the codec is configured with the BEST_COMPRESSION option

  * AnalyzingInfixSuggester now only opens an IndexWriter when changes need to be applied

### Highlights of this Solr release include:

  * "Plugin/Stats" section of the UI doesn't display empty metric types

  * SOLR_SSL_OPTS was mistakenly overwritten in solr.cmd

  * Better validation of filename params in ReplicationHandler

  * Core swapping did not work with new metrics changes in place

  * Admin UI could not find DataImport handlers due to metrics changes

  * AnalyzingInfixSuggester/BlendedInfixSuggester now work with core reload

See the [Lucene CHANGES.txt](/core/6_4_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_4_1/changes/Changes.html) files included
with the release for a full list of details.

## 23 January 2017 - Apache Lucene 6.4.0 and Apache Solr 6.4.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.4.0 and Apache Solr 6.4.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.4.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.4.0>

### Highlights of this Lucene release include:

  * Lucene's best efforts to un-map memory mapped files with "MMapDirectory" now work with the latest Java9 early access builds

  * A new similarity "BooleanSimilarity" that gives terms a score that is equal to their query boost

  * The axiomatic family of similarities (6 in total) based on https://www.eecis.udel.edu/~hfang/pubs/sigir05-axiom.pdf

  * A new token filter "SynonymGraphFilter" that outputs a correct graph structure for multi-token synonyms at query time

  * Graph token streams, such as those produced by the "SynonymGraphFilter", are now handled accurately by query parsers

  * A new collector "DocValuesStatsCollector" gives the ability to compute statistics on DocValues field

  * It is now possible to filter "SortedDocValues" and "SortedSetDocValues" terms enum with a compiled automaton

  * The "UnifiedHighlighter" can now highlight fields with queries that don't necessarily refer to that field

  * DrillSideways can now run queries concurrently

  * Index sorting now supports sorting on multi-valued fields using MIN, MAX, etc. selectors

  * Points do not store the implicit split dimension in the 1-dimension case. This saves between 6% memory for the largest types such an InetAddressPoint to 33% for the smaller types such as HalfFloatPoint.

  * The BKD in-memory index for dimensional points now uses a compressed format, using substantially less RAM in some cases

  * The BKD writing now buffers each leaf block in heap before writing to disk, giving a small speedup in points-heavy use cases

  * "TermAutomatonQuery" now rewrites to more efficient queries when possible

### Highlights of this Solr release include:

Streaming:

  * Addition of a HavingStream to Streaming API and Streaming Expressions

  * Addition of a priority Streaming Expression

  * Streaming expressions now support collection aliases

Machine Learning:

  * Configurable Learning-To-Rank (LTR) support: upload feature definitions, extract feature values, upload your own machine learnt models and use them to rerank search results.

Faceting:

  * Added "param" query type to facet domain filter specification to obtain filters via query parameters

  * Any facet command can be filtered using a new parameter filter. Example:  { type:terms, field:category, filter:"user:yonik" }

Scripts / Command line:

  * A new command-line tool to manage the snapshots functionality

  * bin/solr and bin/solr.cmd now use mkroot command

SolrCloud / SolrJ

  * LukeResponse now supports dynamic fields

  * Solrj client now supports hierarchical clusters and other topics marker

  * Collection backup/restore are extensible.

Security:

  * Support Secure Impersonation / Proxy User for Solr authentication

  * Key Store type can be specified in solr.in.sh file for SSL

  * New generic authentication plugins: 'HadoopAuthPlugin' and 'ConfigurableInternodeAuthHadoopPlugin' that delegate all functionality to Hadoop authentication framework

Query / QueryParser / Highlighting:

  * A new highlighter: The Unified Highlighter.  Try it via `hl.method=unified`; many popular highlighting parameters / features are supported.  It's the highest performing highlighter, especially for large documents.  Highlighting phrase queries and exotic queries are supported equally as well as the Original Highlighter (aka the default/standard one).  Please use this new highlighter and report issues since it will likely become the default one day.

  * Leading wildcard in complexphrase query parser are now accepted and optimized with the `ReversedWildcardFilterFactory` when it's provided

Metrics:

  * Use metrics-jvm library to instrument jvm internals such as GC, memory usage and others.

  * A lot of metrics have been added to the collection: index merges, index store I/Os, query, update, core admin, core load thread pools, shard replication, tlog replay and replicas

  * A new /admin/metrics API to return all metrics collected by Solr via API.

Misc changes:

  * The new config parameter 'maxRamMB'can now limit the memory consumed by the FastLRUCache

  * A new document processor 'SkipExistingDocumentsProcessor' that skips duplicate inserts and ignores updates to missing docs

  * FieldCache information fetched via the mbeans handler or seen via the UI now displays the total size used.

  * A new config flag 'enable' allows to enable/disable any cache

Please note, this release cannot be built from source with Java 8 update 121,
use an earlier version instead! This is caused by a bug introduced into the
Javadocs tool shipped with that update. The workaround was too late for this
Lucene release. Of course, you can use the binary artifacts.

See the [Lucene CHANGES.txt](/core/6_4_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_4_0/changes/Changes.html) files included
with the release for a full list of details.

## 8 November 2016 - Apache Lucene 6.3.0 and Apache Solr 6.3.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.3.0 and Apache Solr 6.3.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.3.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.3.0>

### Highlights of this Lucene release include:

  * A brand new "UnifiedHighlighter" derivative of the PostingsHighlighter that can consume offsets from postings, term vectors, or analysis. It can highlight phrases as accurately as the standard Highlighter. Light term vectors can be used with offsets in postings for fast wildcard (MultiTermQuery) highlighting.

  * SimpleQueryParser now parses '*' to MatchAllDocsQuery

  * FuzzyQuery now matches all terms within the specified edit distance, even if they are short terms

  * Points do not store the implicit split dimension in the 1-dimension case. This saves between 6% memory for the largest types such an InetAddressPoint to 33% for the smaller types such as HalfFloatPoint.

  * Many other changes and bug fixes

### Highlights of this Solr release include:

DocValues, streaming, /export, machine learning

  * Optimize, store and deploy AI models in Solr

  * Ability to add custom streaming expressions

  * New streaming expressions such as "fetch", "executor", and "commit" added.

  * Parallel SQL accepts <, >, =, etc., symbols.

  * Support facet scoring with the scoreNodes expression

  * Retrieving docValues as stored values was sped up by using the proper leaf reader rather than ask for a global view.  In extreme cases, this leads to a 100x speedup.

Faceting:

  * facet.method=enum can bypass exact counts calculation with facet.exists=true, it just returns 1 for terms which exists in result docset

  * Add "overrequest" parameter to JSON Facet API to control amount of overrequest  on a distributed terms facet

Logging:

  * You can now set Solr's log level through environment variable SOLR_LOG_LEVEL

  * GC logs are rotated by JVM to a max of 9 files, and backed up via bin/solr scripts

  * Solr's logging verbosity at the INFO level has been greatly reduced by moving much logging to DEBUG level

  * The solr-8983-console.log file now only logs STDOUT and STDERR output, not all log4j logs as before

  * Solr's main log file, solr.log, is now written to SOLR_LOGS_DIR without changing log4j.properties

Start scripts:

  * Allow 180 seconds for shutdown before killing solr (configurable, old limit 5s) (Unix only)

  * Start scripts now exits with informative message if using wrong Java version

  * Fixed "bin/solr.cmd zk upconfig" command which was broken on windows

  * You can now ask for DEBUG logging simply with '-v' option, and for WARN logging with '-q' option

SolrCloud:

  * The DELETEREPLICA API can accept a 'count' parameter and remove "count" number of replicas from each shard if the shard name is not provided

  * The config API shows expanded useParams for request handlers inline

  * Ability to create/delete/list snapshots at collection level

  * The modify collection API now waits for the modified properties to show up in the cluster state before returning

  * Many bug fixes related to SolrCloud recovery for data safety and faster recovery times.

Security:

  * SolrJ now supports Kerberos delegation tokens

  * Pooled SSL connections were not being re-used. This is now fixed.

  * Fix for the blockUnknown property which made inter-node communication impossible

  * Support SOLR_AUTHENTICATION_OPTS and SOLR_AUTHENTICATION_CLIENT_CONFIGURER in windows bin/solr.cmd script

  * New parameter -u <user:pass> in bin/post to pass basicauth credentials

Misc changes:

  * Optimizations to lower memory allocations when indexing JSON as well as for replication between solr cloud nodes.

  * A new Excel workbook (.xlsx) response writer has been added. Use 'wt=xlsx' request parameter on a query request to enable.

See the [Lucene CHANGES.txt](/core/6_3_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_3_0/changes/Changes.html) files included
with the release for a full list of details.

## 20 September 2016 - Apache Lucene 6.2.1 and Apache Solr 6.2.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.2.1 and Apache Solr 6.2.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.2.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.2.1>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/6_2_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_2_1/changes/Changes.html) files included
with the release for a full list of details.

## 09 September 2016 - Apache Lucene 5.5.3 and Apache Solr 5.5.3 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.3 and Apache Solr 5.5.3

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.3>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.3>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/5_5_3/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_5_3/changes/Changes.html) files included
with the release for a full list of details.

## 25 August 2016 - Apache Lucene 6.2.0 and Apache Solr 6.2.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.2.0 and Apache Solr 6.2.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.2.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.2.0>

### Highlights of this Lucene release include:

  * The CREATE_NEW flag is passed when creating a file to ensure Lucene is really write-once

  * Index numeric ranges (min and max value in a single field) and search by overlapping range

  * IndexWriter methods return a sequence number indicating effective order of operations across threads

  * UkrainianMorfologikAnalyzer is a new dictionary based analyzer for the Ukrainian language

  * The Polygon class can now be created from a GeoJSON string

  * Compound file creation now verifies checksum of its component files

  * Index time sorting is now a core feature, and supports dimensional points

  * StandardAnalyzer is moved to core and is the default analyzer

  * MatchNoDocsQuery now includes the reason it was created

  * QueryParser can now be told to not pre-split on whitespace

  * MMapDirectory tries harder to prevent SIGSEGV if buggy code tries to execute
    searches after the index was closed, but it's still best effort

  * MMapDirectory no longer allocates weak references to ease garbage collection

  * Conjunction (MUST, FILTER) queries are faster

  * Dimensional points have much faster (~40%) flush time and use less space in the index

### Highlights of this Solr release include:

DocValues, streaming, /export, machine learning

  * DocValues can now be used with BoolFields

  * Date and boolean support added to /export handler

  * Add "scoreNodes" streaming graph expression

  * Support parallel ETL with the "topic" expression

  * Feature selection and logistic regression on text via new streaming expressions: "features" and "train"

bin/solr script

  * Add basic auth support to the bin/solr script

  * File operations to/from Zookeeper are now supported

SolrCloud

  * New tag 'role' in replica placement rules, e.g. rule=role:!overseer keeps new repicas off overseer nodes

  * CDCR: fall back to whole-index replication when tlogs are insufficient

  * New REPLACENODE command to decommission an existing node and replace it with another new node

  * New DELETENODE command to delete all replicas on a node

Security

  * Add Kerberos delegation token support

  * Support secure impersonation / proxy user for Kerberos authentication

Misc changes

  * A large number of regressions were fixed in the new Admin UI

  * New boolean comparison function queries comparing numeric arguments: gt, gte, lt, lte, eq

  * Upgraded Extraction module to Apache Tika 1.13.

  * Updated to Hadoop 2.7.2

See the [Lucene CHANGES.txt](/core/6_2_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_2_0/changes/Changes.html) files included
with the release for a full list of details.

## 25 June 2016 - Apache Lucene 5.5.2 and Apache Solr 5.5.2 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.2 and Apache Solr 5.5.2

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.2>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.2>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/5_5_2/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_5_2/changes/Changes.html) files included
with the release for a full list of details.

## 17 June 2016 - Apache Lucene 6.1.0 and Apache Solr 6.1.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.1.0 and Apache Solr 6.1.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.1.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.1.0>

### Highlights of this Lucene release include:

  * Numerous improvements to LatLonPoint, for indexing a latitude/longitude point and searching by polygon, distance or box, or finding nearest neighbors

  * Geo3D now has simple APIs for creating common shape queries, matching LatLonPoint

  * Faster indexing and searching of points.

  * Faster geo-spatial indexing and searching for LatLonPoint, Geo3D and GeoPoint (see http://home.apache.org/~mikemccand/geobench.html )

  * HardlinkCopyDirectoryWrapper optimizes file copies using hard links

  * In case of contention, the query cache now prefers returning an uncached Scorer rather than waiting on a lock.

### Highlights of this Solr release include:

 * Added graph traversal support, and new "sort" and "random" streaming expressions. It's also now possible to create streaming expressions with the Solr Admin UI.

 * Fixed the ENUM faceting method to not be unnecessarily rewritten to FCS, which was causing slowdowns.

 * Reduced garbage creation when creating cache entries.

 * New [subquery] document transformer to obtatin related documents per result doc.

 * EmbeddedSolrServer allocates heap much wisely even with plain document list without callbacks.

 * New GeoJSON response writer for encoding geographic data in query responses.

See the [Lucene CHANGES.txt](/core/6_1_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_1_0/changes/Changes.html) files included
with the release for a full list of details.

## 28 May 2016 - Apache Lucene 6.0.1 and Apache Solr 6.0.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.0.1 and Apache Solr 6.0.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.0.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.0.1>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/6_0_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/6_0_1/changes/Changes.html) files included
with the release for a full list of details.

## 5 May 2016 - Apache Lucene 5.5.1 and Apache Solr 5.5.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.1 and Apache Solr 5.5.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.1>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/5_5_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_5_1/changes/Changes.html) files included
with the release for a full list of details.

## 8 April 2016 - Apache Lucene 6.0.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 6.0.0 and Apache Solr 6.0.0

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/6.0.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/6.0.0>

### Highlights of this Lucene release include:

  * Java 8 is the minimum Java version required.

  * Dimensional points, replacing legacy numeric fields, provides fast and space-efficient support for both single- and multi-dimension range and shape filtering.  This includes numeric (int, float, long, double), InetAddress, BigInteger and binary range filtering, as well as geo-spatial shape search over indexed 2D LatLonPoints.  See [this blog post](https://www.elastic.co/blog/lucene-points-6.0) for details.  Dependent classes and modules (e.g., MemoryIndex, Spatial Strategies, Join module) have been refactored to use new point types.

  * Lucene classification module now works on Lucene Documents using a KNearestNeighborClassifier or SimpleNaiveBayesClassifier.

  * The spatial module no longer depends on third-party libraries. Previous spatial classes have been moved to a new spatial-extras module.

  * Spatial4j has been updated to a new 0.6 version hosted by locationtech.

  * TermsQuery performance boost by a more aggressive default query caching policy.

  * IndexSearcher's default Similarity is now changed to BM25Similarity.

  * Easier method of defining custom CharTokenizer instances.

### Highlights of this Solr release include:

  * Improved defaults for "Similarity" used in Solr, in order to provide better default experience for new users.

  * Improved "Similarity" defaults for users upgrading: DefaultSimilarityFactory has been removed, implicit default Similarity has been changed to SchemaSimilarityFactory, and SchemaSimilarityFactory has been modified to use BM25Similarity as the default for field types that do not explicitly declare a Similarity.

  * Deprecated GET methods for schema are now accessible through the bulk API. The output has less details and is not backward compatible.

  * Users should set useDocValuesAsStored="false" to preserve sort order on multi-valued fields that have both stored="true" and docValues="true".

  * Formatted date-times are more consistent with ISO-8601. BC dates are now better supported since they are now formatted with a leading '-'. AD years after 9999 have a leading '+'. Parse exceptions have been improved.

  * Deprecated SolrServer and subclasses have been removed, use SolrClient instead.

  * The deprecated <nrtMode> configuration in solrconfig.xml has been removed. Users must remove it from solrconfig.xml.

  * SolrClient.shutdown() has been removed, use SolrClient.close() instead.

  * The deprecated zkCredientialsProvider element in solrcloud section of solr.xml is now removed. Use the correct spelling (zkCredentialsProvider) instead.

  * Added support for executing Parallel SQL queries across SolrCloud collections. Includes StreamExpression support and a new JDBC Driver for the SQL Interface.

  * New features and capabilities added to the streaming API.

  * Added support for SELECT DISTINCT queries to the SQL interface.

  * New GraphQuery to enable graph traversal as a query operator.

  * New support for Cross Data Center Replication consisting of active/passive replication for separate SolrClouds hosted in separate data centers.

  * Filter support added to Real-time get.

  * Column alias support added to the Parallel SQL Interface.

  * New command added to switch between non/secure mode in zookeeper.

  * Now possible to use IP fragments in replica placement rules.

## 22 February 2016 - Apache Lucene 5.5.0 and Apache Solr 5.5.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.5.0 and Apache Solr 5.5.0

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.5.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.5.0>

### Highlights of this Lucene release include:

* JoinUtil.createJoinQuery can now join on numeric doc values fields

* BlendedInfixSuggester now has an exponential reciprocal scoring model, to more strongly favor suggestions with matches closer to the beginning

* CustomAnalyzer has improved (compile time) type safety

* DFISimilarity implements the divergence from independence scoring model

* Fully wrap any other merge policy using MergePolicyWrapper

* Sandbox geo point queries have graduated into the spatial module, and now use a more efficient binary term encoding for smaller index size, faster indexing, and decreased search-time heap usage

* BooleanQuery performs some new query optimizations

* TermsQuery constructors are more GC efficient

### Highlights of this Solr release include:

* The schema version has been increased to 1.6, and Solr now returns non-stored doc values fields along with stored fields

* The PERSIST CoreAdmin action has been removed

* The mergePolicy element is deprecated in favor of a similar mergePolicyFactory element, in solrconfig.xml

* CheckIndex now works on HdfsDirectory

* RuleBasedAuthorizationPlugin now allows wildcards in the role, and accepts an 'all' permission

* Users can now choose compression mode in SchemaCodecFactory

* Solr now supports Lucene's XMLQueryParser

* Collections APIs now have async support

* Uninverted field faceting is re-enabled, for higher performance on rarely changing indices


## 23 January 2016 - Apache Lucene 5.3.2 and Apache Solr 5.3.2 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.3.2 and Apache Solr 5.3.2

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.3.2>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.3.2>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/5_3_2/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_3_2/changes/Changes.html) files included
with the release for a full list of details.

## 23 January 2016 - Apache Lucene 5.4.1 and Apache Solr 5.4.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.4.1 and Apache Solr 5.4.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.4.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.4.1>

This release contains an important fix for a corruption bug that was
introduced in version 5.4.0. If you are on 5.4.0 and using BINARY,
SORTED_NUMERIC or SORTED_SET doc values, upgrading to 5.4.1 is strongly
recommended.

See the [Lucene CHANGES.txt](/core/5_4_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_4_1/changes/Changes.html) files included
with the release for a full list of details.

## 14 December 2015 - Apache Lucene 5.4.0 and Apache Solr 5.4.0 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.4.0 and Apache Solr 5.4.0

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.4.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.4.0>

### Highlights of this Lucene release include:
####API Changes
* Query.getBoost and Query.setBoost are deprecated in favour of the new BoostQuery
* The Filter class is deprecated in favour of FILTER clauses in a BooleanQuery
* DefaultSimilarity has been renamed to ClassicSimilarity to prepare for the move to BM25 in Lucene 6

####New features
* New Serbian token filter
* New DecimalDigitFilter, to fold unicode digits to latin digits
* New UnicodeWhitespaceTokenizer, that uses Unicode's whitespace definition and splits on NBSP
* New GeoPointDistanceRangeQuery to search for geo-points within a ring
* Query caching is now enabled by default in IndexSearcher, use IndexSearcher.setQueryCache(null) to disable

####Optimizations
* MatchAllDocsQuery got faster
* Doc values now use less memory for multi-valued fields and less disk in case of sparse fields
* Two-phase iterators got a match cost API so that the costly bits can be checked last

####Bug fixes
* PatternTokenizer no longer hangs onto heap sized to the maximum input string it's ever seen.

### Highlights of this Solr release include:
####UI Changes
* The rearchitected Admin UI is now prominently linked to from the existing UI, and includes support for managing collections as well as creating and removing fields via the schema tab. Expect it to be default in the next release.

####API Features
* New Collections APIs for migrating from clusterstate.json to per-collection state.json and forcing the election of a leader when all replicas in a shard are down.
* A new configset management API has been added.

####Querying Features
* Filter cache is now accessible via a solr query syntax.
* ScoreJoins can now refer to a single-sharded collection that is replicated on all nodes.
* Add boost support, and 'exclude the queried document' in MoreLikeThis QParser.
* Add a 'sort' local param to the collapse QParser to support using complex sort options to select the representitive doc for each collapsed group.

####Other Features
* SolrJ now has support for connecting to Solr using basic authentication.
* Analyzing suggesters can now filter suggestions by a context field.
* JSON Facet API: add "method" param to terms/field facets to give an execution hint for what method should be used to facet.
* CloneFieldUpdateProcessorFactory now supports choosing a "dest" field name based on a regex pattern and replacement init options.
* Provide pluggable context tool support for VelocityResponseWriter.

## 24 September 2015 - Apache Lucene 5.3.1 and Apache Solr 5.3.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.3.1 and Apache Solr 5.3.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.3.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.3.1>

### Highlights of this Lucene release include:
#### Bug Fixes

* Remove classloader hack in MorfologikFilter
* UsageTrackingQueryCachingPolicy no longer caches trivial queries like MatchAllDocsQuery
* Fixed BoostingQuery to rewrite wrapped queries

### Highlights of this Solr release include:
#### Bug Fixes

* security.json is not loaded on server start
* RuleBasedAuthorization plugin does not work for the collection-admin-edit permission
* VelocityResponseWriter template encoding issue. Templates must be UTF-8 encoded
* SimplePostTool (also bin/post) -filetypes "*" now works properly in 'web' mode
* example/files update-script.js to be Java 7 and 8 compatible.
* SolrJ could not make requests to handlers with '/admin/' prefix
* Use of timeAllowed can cause incomplete filters to be cached and incorrect results to be returned on subsequent requests
* VelocityResponseWriter's $resource.get(key,baseName,locale) to use specified locale.
* Resolve XSS issue in Admin UI stats page


## 24 August 2015 - Apache Lucene 5.3.0 and Apache Solr 5.3.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 5.3.0 and Apache Solr 5.3.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.3.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.3.0>

### Highlights of this Lucene release include:
#### API Changes

 * PhraseQuery and BooleanQuery are now immutable

#### New features

 * Added a new org.apache.lucene.search.join.CheckJoinIndex class that can be used to validate that an index has an appropriate structure to run join queries
 * Added a new BlendedTermQuery to blend statistics across several terms
 * New common suggest API that mirrors Lucene's Query/IndexSearcher APIs for Document based suggester.
 * IndexWriter can now be initialized from an already open near-real-time or non-NRT reader
 * Add experimental range tree doc values format and queries, based on a 1D version of the spatial BKD tree, for a faster and smaller alternative to postings-based numeric and binary term filtering.  Range trees can also handle values larger than 64 bits.

#### Geo-related features and improvements

 * Added GeoPointField, GeoPointInBBoxQuery, GeoPointInPolygonQuery for simple "indexed lat/lon point in bbox/shape" searching
 * Added experimental BKD geospatial tree doc values format and queries, for fast "bbox/polygon contains lat/lon points"
 * Use doc values to post-filter GeoPointField hits that fall in boundary cells, resulting in smaller index, faster searches and less heap used for each query

#### Optimizations
 * Reduce RAM usage of FieldInfos, and speed up lookup by number, by using an array instead of TreeMap except in very sparse cases
 * Faster intersection of the terms dictionary with very finite automata, which can be generated eg. by simple regexp queries
 * Various bugfixes and optimizations since the 5.2.0 release.

### Highlights of this Solr release include:
* In addition to many other improvements in the security framework, Solr now includes an AuthenticationPlugin implementing HTTP Basic Auth that stores credentials securely in ZooKeeper. This is a simple way to require a username and password for anyone accessing Solr’s admin screen or APIs.
* In built AuthorizationPlugin that provides fine grained control over implementing ACLs for various resources with permisssion rules which are stored in ZooKeeper.
* The JSON Facet API can now change the domain for facet commands, essentially doing a block join and moving from parents to children, or children to parents before calculating the facet data.
* Major improvements in performance of the new Facet Module / JSON Facet API.
* Query and Range Facets under Pivot Facets. Just like the JSON Facet API, pivot facets can how nest other facet types such as range and query facets.
* More Like This Query Parser options. The MoreLikeThis QParser now supports all options provided by the MLT Handler. The query parser is much more versatile than the handler as it works in cloud mode as well as anywhere a normal query can be specified.
* Added Schema API support in SolrJ
* Added Scoring mode for query-time join and block join.
* Added Smile response format

See the [Lucene CHANGES.txt](/core/5_3_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_3_0/changes/Changes.html) files included
with the release for a full list of details.

## 15 June 2015 - Apache Lucene 5.2.1 and Apache Solr 5.2.1 Available

The Lucene PMC is pleased to announce the release of Apache Lucene 5.2.1 and Apache Solr 5.2.1

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.2.1>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.2.1>

### Highlights of this Lucene release include:
* Fix class loading deadlock relating to Codec initialization, default codec and SPI discovery.
* NRT readers now reflect a new commit even if there is no change to the commit user data
* Queries now get a dummy Similarity when scores are not needed in order to not load unnecessary information like norms

### Highlights of this Solr release include:
* Fix javascript bug introduced by SOLR-7409 that breaks the dataimport screen in the admin UI
* Faceting on a numeric field with a unique() subfacet function on another numeric field can result in incorrect results or an exception
* New Facet Module should respect shards.tolerant and process all non-failing shards instead of throwing an exception
* A request with a json content type but no body caused a null pointer exception
* SolrOutputFormat creates an invalid solr.xml in the solr home zip for MapReduceIndexerTool
* Fix new (Angular-based) admin UI Cloud pane
* The DefaultSolrHighlighter since 5.0 was determining if payloads were present in a way that was slow, especially when lots of fields were highlighted. It's now fast
* Requests are not distributed evenly if the collection isn't present locally

See the [Lucene CHANGES.txt](/core/5_2_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_2_1/changes/Changes.html) files included
with the release for a full list of details.

## 7 June 2015 - Apache Lucene 5.2.0 and Apache Solr 5.2.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 5.2.0 and Apache Solr 5.2.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.2.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.2.0>

### Highlights of this Lucene release include:

* Span queries now share document conjunction/intersection code with boolean queries, and use two-phased iterators for faster intersection by avoiding loading positions in certain cases.

* Added two-phase support to SpanNotQuery, and SpanPositionCheckQuery and its subclasses: SpanPositionRangeQuery, SpanPayloadCheckQuery, SpanNearPayloadCheckQuery, SpanFirstQuery.

* Added a new query time join to the join module that uses global ordinals, which is faster for subsequent joins between reopens.

* New CompositeSpatialStrategy combines speed of RPT with accuracy of SDV. Includes optimized Intersect predicate to avoid many geometry checks. Uses TwoPhaseIterator.

* New LimitTokenOffsetFilter that limits tokens to those before a configured maximum start offset.

* New spatial PackedQuadPrefixTree, a generally more efficient choice than QuadPrefixTree, especially for high precision shapes. When used, you should typically disable RPT's pruneLeafyBranches option.

* Expressions now support bindings keys that look like zero arg functions

* Add SpanWithinQuery and SpanContainingQuery that return spans inside of / containing another spans.

* New Spatial "Geo3d" API with partial Spatial4j integration. It is a set of shapes implemented using 3D planar geometry for calculating spatial relations on the surface of a sphere. Shapes include Point, BBox, Circle, Path (buffered line string), and Polygon.

* Various bugfixes and optimizations since the 5.1.0 release.

### Highlights of this Solr release include:

* Restore API allows restoring a core from an index backup.

* JSON Facet API
    * unique() is now implemented for numeric and date fields
    * Optional flatter form via a "type" parameter
    * Added support for "mincount" parameter in range facets to suppress buckets less than that count
    * Multi-select faceting support for the Facet Module via the "excludeTags" parameter which disregards any matching tagged filters for that facet.
    * hll() facet function for distributed cardinality via HyperLogLog algorithm.
    See examples at http://yonik.com/solr-count-distinct/

* A new "facet.range.method" parameter to let users choose how to do range faceting between an implementation based on filters (previous algorithm, using "facet.range.method=filter") or DocValues ("facet.range.method=dv")

* Rule-based Replica assignment during collection, shard, and replica creation.

* Stats component:
    * New 'cardinality' option for stats.field, uses HyperLogLog to efficiently estimate the cardinality of a field w/bounded RAM. Blog post: https://lucidworks.com/blog/hyperloglog-field-value-cardinality-stats/
    * stats.field now supports individual local params for 'countDistinct' and 'distinctValues'. 'calcdistinct' is still supported as an alias for both options.

* Solr security
    * Authentication and Authorization frameworks that define interfaces, and mechanisms to create, load, and use authorization/authentication plugins have been added.
    * A Kerberos authentication plugin which would allow running a Kerberized Solr setup.

* Solr Streaming Expressions
   See https://cwiki.apache.org/confluence/display/solr/Streaming+Expressions

* bin/post (and SimplePostTool in -Dauto=yes mode) now sends rather than skips files without a known content type, as "application/octet-stream", provided it still is in the allowed filetypes setting.

* HDFS transaction log replication factor is now configurable

* A cluster-wide property can now be be added/edited/deleted using the zkcli script and doesn't require a running Solr instance.

* New spatial RptWithGeometrySpatialField, based on CompositeSpatialStrategy, which blends RPT indexes for speed with serialized geometry for accuracy.  Includes a Lucene segment based in-memory shape cache.

* Refactored Admin UI using AngularJS. It isn't the default, but a parallel UI interface in this release.

* Solr has internally been upgraded to use Jetty 9.

Both releases contain a number of new features, bug fixes, and optimizations.

See the [Lucene CHANGES.txt](/core/5_2_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_2_0/changes/Changes.html) files included
with the release for a full list of details.

## 14 April 2015 - Apache Lucene 5.1.0 and Apache Solr 5.1.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 5.1.0 and Apache Solr 5.1.0.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/5.1.0>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/5.1.0>

Both releases contain a number of new features, bug fixes, and optimizations.

See the [Lucene CHANGES.txt](/core/5_1_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_1_0/changes/Changes.html) files included
with the release for a full list of details.

## 5 March 2015 - Apache Lucene 4.10.4 and Apache Solr 4.10.4 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.10.4 and Apache Solr 4.10.4.

Lucene can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/java/4.10.4>
and Solr can be downloaded from <http://www.apache.org/dyn/closer.lua/lucene/solr/4.10.4>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_10_4/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_10_4/changes/Changes.html) files included
with the release for a full list of details.

## 20 February 2015 - Apache Lucene 5.0.0 and Apache Solr 5.0.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 5.0.0 and Apache Solr 5.0.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

See the [Lucene CHANGES.txt](/core/5_0_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/5_0_0/changes/Changes.html) files included
with the release for a full list of details.

### Highlights of the Lucene release include:

Stronger index safety

* All file access now uses Java’s NIO.2 APIs which give Lucene stronger index safety in terms of better error handling and safer commits.

* Every Lucene segment now stores a unique id per-segment and per-commit to aid in accurate replication of index files.

* During merging, IndexWriter now always checks the incoming segments for corruption before merging. This can mean, on upgrading to 5.0.0, that merging may uncover long-standing latent corruption in an older 4.x index.

Reduced heap usage

* Lucene now supports random-writable and advance-able sparse bitsets (RoaringDocIdSet and SparseFixedBitSet), so the heap required is in proportion to how many bits are set, not how many total documents exist in the index.

* Heap usage during IndexWriter merging is also much lower with the new Lucene50Codec, since doc values and norms for the segments being merged are no longer fully loaded into heap for all fields; now they are loaded for the one field currently being merged, and then dropped.

* The default norms format now uses sparse encoding when appropriate, so indices that enable norms for many sparse fields will see a large reduction in required heap at search time.

* 5.0 has a new API to print a tree structure showing a recursive breakdown of which parts are using how much heap.

Other features

* FieldCache is gone (moved to a dedicated UninvertingReader in the misc module). This means when you intend to sort on a field, you should index that field using doc values, which is much faster and less heap consuming than FieldCache.

* Tokenizers and Analyzers no longer require Reader on init.

* NormsFormat now gets its own dedicated NormsConsumer/Producer

* SortedSetSortField, used to sort on a multi-valued field, is promoted from sandbox to Lucene's core.

* PostingsFormat now uses a "pull" API when writing postings, just like doc values. This is powerful because you can do things in your postings format that require making more than one pass through the postings such as iterating over all postings for each term to decide which compression format it should use.

* New DateRangeField type enables Indexing and searching of date ranges, particularly multi-valued ones.

* A new ExitableDirectoryReader extends FilterDirectoryReader and enables exiting requests that take too long to enumerate over terms.

* Suggesters from multi-valued field can now be built as DocumentDictionary now enumerates each value separately in a multi-valued field.

* ConcurrentMergeScheduler detects whether the index is on SSD or not and does a better job defaulting its settings. This only works on Linux for now; other OS's will continue to use the previous defaults (tuned for spinning disks).

* Auto-IO-throttling has been added to ConcurrentMergeScheduler, to rate limit IO writes for each merge depending on incoming merge rate.

* CustomAnalyzer has been added that allows to configure analyzers like you do in Solr's index schema. This class has a builder API to configure Tokenizers, TokenFilters, and CharFilters based on their SPI names and parameters as documented by the corresponding factories.

* Memory index now supports payloads.

* Added a filter cache with a usage tracking policy that caches filters based on frequency of use.

* The default codec has an option to control BEST_SPEED or BEST_COMPRESSION for stored fields.

* Stored fields are merged more efficiently, especially when upgrading from previous versions or using SortingMergePolicy

### Highlights of the Solr release include:

* Usability improvements that include improved bin scripts and new and restructured examples.

* Scripts to support installing and running Solr as a service on Linux.

* Distributed IDF is now supported and can be enabled via the config. Currently, there are four supported implementations for the same:
    * LocalStatsCache: Local document stats.
    * ExactStatsCache: One time use aggregation
    * ExactSharedStatsCache: Stats shared across requests
    * LRUStatsCache: Stats shared in an LRU cache across requests

* Solr will no longer ship a war file and instead be a downloadable application.

* SolrJ now has first class support for Collections API.

* Implicit registration of replication,get and admin handlers.

* Config API that supports paramsets for easily configuring solr parameters and configuring fields. This API also supports managing of pre-existing request handlers and editing common solrconfig.xml via overlay.

* API for managing blobs allows uploading request handler jars and registering them via config API.

* BALANCESHARDUNIQUE Collection API that allows for even distribution of custom replica properties.

* There's now an option to not shuffle the nodeSet provided during collection creation.

* Option to configure bandwidth usage by Replication handler to prevent it from using up all the bandwidth.

* Splitting of clusterstate to per-collection enables scalability improvement in SolrCloud. This is also the default format for new Collections that would be created going forward.

* timeAllowed is now used to prematurely terminate requests during query expansion and SolrClient request retry.

* pivot.facet results can now include nested stats.field results constrained by those pivots.

* stats.field can be used to generate stats over the results of arbitrary numeric functions.
  It also allows for requesting for statistics for pivot facets using tags.

* A new DateRangeField has been added for indexing date ranges, especially multi-valued ones.

* Spatial fields that used to require units=degrees now take distanceUnits=degrees/kilometers miles instead.

* MoreLikeThis query parser allows requesting for documents similar to an existing document and also works in SolrCloud mode.

* Logging improvements:
    * Transaction log replay status is now logged
    * Optional logging of slow requests.

## 29 December 2014 - Apache Lucene 4.10.3 and Apache Solr 4.10.3 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.10.3 and Apache Solr 4.10.3.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes. The Solr release includes a security vulnerability
fix that you can read about on the Solr news page: <http://lucene.apache.org/solr/news.html>

See the [Lucene CHANGES.txt](/core/4_10_3/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_10_3/changes/Changes.html) files included
with the release for a full list of details, and Happy Holidays!

## 31 October 2014 - Apache Lucene 4.10.2 and Apache Solr 4.10.2 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.10.2 and Apache Solr 4.10.2.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_10_2/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_10_2/changes/Changes.html) files included
with the release for a full list of details, and Happy Halloween!

## 29 September 2014 - Apache Lucene 4.10.1 and Apache Solr 4.10.1 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.10.1 and Apache Solr 4.10.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_10_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_10_1/changes/Changes.html) files included
with the release for a full list of details.

## 22 September 2014 - Apache Lucene 4.9.1 and Apache Solr 4.9.1 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.9.1 and Apache Solr 4.9.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_9_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_9_1/changes/Changes.html) files included
with the release for a full list of details.

## 03 September 2014 - Apache Lucene 4.10.0 and Apache Solr 4.10.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.10.0 and Apache Solr 4.10.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

See the [Lucene CHANGES.txt](/core/4_10_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_10_0/changes/Changes.html) files included
with the release for a full list of details.

### Highlights of the Lucene release include:

* New TermAutomatonQuery using an automaton for proximity queries.
  <http://blog.mikemccandless.com/2014/08/a-new-proximity-query-for-lucene-using.html>

* New OrdsBlockTree terms dictionary supporting ord lookup.

* Simplified matchVersion handling for Analyzers with new setVersion method, as well as Analyzer constructors not requiring Version.

* Fixed possible corruption when opening a 3.x index with NRT reader.

* Fixed edge case in StandardTokenizer that caused extremely slow parsing times with long text which partially matched grammar rules.

### Highlights of the Solr release include:

* This release upgrades Solr Cell's (contrib/extraction) dependency
  on Apache POI to mitigate
  [2 security vulnerabilities](/solr/solrnews.html#18-august-2014-recommendation-to-update-apache-poi-in-apache-solr-480-481-and-490-installations).

* Scripts for starting, stopping, and running Solr examples

* Distributed query support for facet.pivot

* Interval Faceting for Doc Values fields

* New "terms" QParser for efficiently filtering documents by a list of values

## 18 August 2014 - Recommendation to update Apache POI in Apache Solr 4.8.0, 4.8.1, and 4.9.0 installations

Apache Solr versions 4.8.0, 4.8.1, 4.9.0 bundle Apache POI 3.10-beta2 with its binary release tarball.
This version (and all previous ones) of Apache POI are vulnerable to the following issues:
CVE-2014-3529 *(XML External Entity (XXE) problem in Apache POI's OpenXML parser)*,
CVE-2014-3574 *(XML Entity Expansion (XEE) problem in Apache POI's OpenXML parser)*.

The Apache POI PMC released a bugfix version (3.10.1) today.

Solr users are affected by these issues, if they enable the "Apache Solr Content Extraction Library (Solr Cell)"
contrib module from the folder "contrib/extraction" of the release tarball.

Users of Apache Solr are strongly advised to keep the module disabled if they don't use it.
Alternatively, users of Apache Solr 4.8.0, 4.8.1, or 4.9.0 can update the affected libraries by
replacing the vulnerable JAR files in the distribution folder. Users of previous versions have
to update their Solr release first, patching older versions is impossible.

For detailed instructions, see [Solr's News](/solr/solrnews.html#18-august-2014-recommendation-to-update-apache-poi-in-apache-solr-480-481-and-490-installations)

## 25 June 2014 - Apache Lucene 4.9.0 and Apache Solr 4.9.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.9.0 and Apache Solr 4.9.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

See the [Lucene CHANGES.txt](/core/4_9_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_9_0/changes/Changes.html) files included
with the release for a full list of details.

### Highlights of the Lucene release include:

* New Terms.getMin/Max methods to retrieve the lowest and highest
  terms per field.

* New IDVersionPostingsFormat, optimized for ID lookups that associate
  a monotonically increasing version per ID.

* Atomic update of a set of doc values fields.

* Numerous optimizations for doc values search-time performance.

* New (default) Lucene49NormsFormat to better compress certain cases
  such as very short fields.

* New SORTED_NUMERIC docvalues type for efficient processing of
  multi-valued numeric fields.

* Indexer passes previous token stream for easier reuse.

* MoreLikeThis accepts multiple values per field.

* All classes that estimate their RAM usage now implement a new
  Accountable interface.

* Lucene files are now written by (File)OutputStream on all platforms,
  completely disallowing seeking with simplified IO APIs.

* Improve the confusing error message when MMapDirectory cannot create
  a new map.

### Highlights of the Solr release include:

* Numerous optimizations for doc values search-time performance

* Allow a client application to request the minium achieved replication
  factor for an update request (single or batch) by sending an optional
  parameter "min_rf".

* Query re-ranking support with the new ReRankingQParserPlugin.

* A new [child ...] DocTransformer for optionally including Block-Join
  decendent documents inline in the results of a search.

* A new (default) Lucene49NormsFormat to better compress certain cases
  such as very short fields.

## 11 June 2014 - Open Relevance sub-project closed
The Apache Lucene Project Management Committee decided in a vote,
that the Apache Lucene sub-project "Open Relevance" will be discontinued. There was only modest activity during the last
years and the project made no releases. Thank you to all committers for their support in this project!

## 20 May 2014 - Apache Lucene 4.8.1 and Apache Solr 4.8.1 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.8.1 and Apache Solr 4.8.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_8_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_8_1/changes/Changes.html) files included
with the release for a full list of details.

## 28 April 2014 - Apache Lucene 4.8.0 and Apache Solr 4.8.0 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.8.0 and Apache Solr 4.8.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases now require Java 7 or greater (recommended is
Oracle Java 7 or OpenJDK 7, minimum update 55; earlier versions
have known JVM bugs affecting Lucene and Solr). In addition,
both are fully compatible with Java 8.

See the [Lucene CHANGES.txt](/core/4_8_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_8_0/changes/Changes.html) files included
with the release for a full list of details.

### Highlights of the Lucene release include:

* All index files now store end-to-end checksums, which are
  now validated during merging and reading. This ensures that
  corruptions caused by any bit-flipping hardware problems or bugs
  in the JVM can be detected earlier.  For full detection be sure
  to enable all checksums during merging (it's disabled by default).

* Lucene has a new Rescorer/QueryRescorer API to perform second-pass
  rescoring or reranking of search results using more expensive scoring
  functions after first-pass hit collection.

* AnalyzingInfixSuggester now supports near-real-time autosuggest.

* Simplified impact-sorted postings (using SortingMergePolicy and
  EarlyTerminatingCollector) to use Lucene's Sort class
  to express the sort order.

* Bulk scoring and normal iterator-based scoring were separated,
  so some queries can do bulk scoring more effectively.

* Switched to MurmurHash3 to hash terms during indexing.

* IndexWriter now supports updating of binary doc value fields.

* HunspellStemFilter now uses 10 to 100x less RAM. It also loads
  all known OpenOffice dictionaries without error.

* Lucene now also fsyncs the directory metadata on commits, if the
  operating system and file system allow it (Linux, MacOSX are
  known to work).

* Lucene now uses Java 7 file system functions under the hood,
  so index files can be deleted on Windows, even when readers are
  still open.

* A serious bug in NativeFSLockFactory was fixed, which could
  allow multiple IndexWriters to acquire the same lock.  The
  lock file is no longer deleted from the index directory
  even when the lock is not held.

### Highlights of the Solr release include:

* <code class="inline">&lt;fields&gt;</code> and <code class="inline">&lt;types&gt;</code> tags have been deprecated from schema.xml.
  There is no longer any reason to keep them in the schema file,
  they may be safely removed. This allows intermixing of <code class="inline">&lt;fieldType&gt;</code>,
  <code class="inline">&lt;field&gt;</code> and <code class="inline">&lt;copyField&gt;</code> definitions if desired.

* The new \{!complexphrase\} query parser supports wildcards, ORs etc.
  inside Phrase Queries.

* New Collections API CLUSTERSTATUS action reports the status of
  collections, shards, and replicas, and also lists collection
  aliases and cluster properties.

* Added managed synonym and stopword filter factories, which enable
  synonym and stopword lists to be dynamically managed via REST API.

* JSON updates now support nested child documents, enabling \{!child\}
  and \{!parent\} block join queries.

* Added ExpandComponent to expand results collapsed by the
  CollapsingQParserPlugin, as well as the parent/child relationship
  of nested child documents.

* Long-running Collections API tasks can now be executed
  asynchronously; the new REQUESTSTATUS action provides status.

* Added a hl.qparser parameter to allow you to define a query parser
  for hl.q highlight queries.

* In Solr single-node mode, cores can now be created using named
  configsets.

* New DocExpirationUpdateProcessorFactory supports computing an
  expiration date for documents from the "TTL" expression, as well as
  automatically deleting expired documents on a periodic basis.


## 15 April 2014 - Apache Lucene 4.7.2 and Apache Solr 4.7.2 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.7.2 and Apache Solr 4.7.2.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_7_2/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_7_2/changes/Changes.html) files included
with the release for a full list of details.

## 02 April 2014 - Apache Lucene 4.7.1 and Apache Solr 4.7.1 Available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.7.1 and Apache Solr 4.7.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_7_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_7_1/changes/Changes.html) files included
with the release for a full list of details.

## 12 March 2014 - Apache Lucene 4.8 and Apache Solr 4.8 will require Java 7

The Apache Lucene/Solr committers decided with a large majority on the vote to require **Java 7** for the next minor release of Apache Lucene and Apache Solr (version 4.8)!

The next release will also contain some improvements for Java 7:

* Better file handling (especially on Windows) in the directory implementations. Files can now be deleted on windows, although the index is still open - like it was always possible on Unix environments (delete on last close semantics).

* Speed improvements in sorting comparators: Sorting now uses Java 7's own comparators for integer and long sorts, which are highly optimized by the Hotspot VM.

If you want to stay up-to-date with Lucene and Solr, you should upgrade your infrastructure to Java 7.
Please be aware that you must use at least use Java 7u1.
The recommended version at the moment is Java 7u25. Later versions like 7u40, 7u45,... have a bug causing index corrumption.
Ideally use the Java 7u60 prerelease, which has fixed this bug. Once 7u60 is out, this will be the recommended version.
In addition, there is no more Oracle/BEA JRockit available for Java 7, use the official Oracle Java 7.
JRockit was never working correctly with Lucene/Solr (causing index corrumption), so this should not be an issue.
Please also review our list of JVM bugs: <http://wiki.apache.org/lucene-java/JavaBugs>

*EDIT (as of 15 April 2014):* The recently released Java 7u55 fixes the above bug causing index corrumption.
This version is now the recommended version for running Apache Lucene and Solr.

## 26 February 2014 - Apache Lucene 4.7.0 and Apache Solr<span style="vertical-align: super; font-size: xx-small">TM</span> 4.7.0 available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.7.0 and Apache Solr 4.7.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_7_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_7_0/changes/Changes.html) files included
with the release for a full list of details.

## 28 January 2014 - Apache Lucene 4.6.1 and Apache Solr<span style="vertical-align: super; font-size: xx-small">TM</span> 4.6.1 available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.6.1 and Apache Solr 4.6.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_6_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_6_1/changes/Changes.html) files included
with the release for a full list of details.

## 24 November 2013 - Apache Lucene 4.6.0 and Apache Solr<span style="vertical-align: super; font-size: xx-small">TM</span> 4.6.0 available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.6.0 and Apache Solr 4.6.0.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_6_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_6_0/changes/Changes.html) files included
with the release for a full list of details.

## 24 October 2013 - Apache Lucene 4.5.1 and Apache Solr<span style="vertical-align: super; font-size: xx-small">TM</span> 4.5.1 available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.5.1 and Apache Solr 4.5.1.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

Both releases contain a number of bug fixes.

See the [Lucene CHANGES.txt](/core/4_5_1/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_5_1/changes/Changes.html) files included
with the release for a full list of details.

## 5 October 2013 - Apache Lucene 4.5 and Apache Solr<span style="vertical-align: super; font-size: xx-small">TM</span> 4.5 available

The Lucene PMC is pleased to announce the availability
of Apache Lucene 4.5 and Apache Solr 4.5.

Lucene can be downloaded from <http://lucene.apache.org/core/mirrors-core-latest-redir.html>
and Solr can be downloaded from <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>

See the [Lucene CHANGES.txt](/core/4_5_0/changes/Changes.html) and
[Solr CHANGES.txt](/solr/4_5_0/changes/Changes.html) files included
with the release for a full list of details.

### Highlights of the Lucene release include:

* Added support for missing values to DocValues fields through
  AtomicReader.getDocsWithField.

* Lucene 4.5 has a new Lucene45Codec with Lucene45DocValues, supporting missing
  values and with most datastructures residing off-heap.

* New in-memory DocIdSet implementations which are especially better than
  FixedBitSet on small sets: WAH8DocIdSet, PFORDeltaDocIdSet and EliasFanoDocIdSet.

* CachingWrapperFilter now caches filters with WAH8DocIdSet by default, which
  has the same memory usage as FixedBitSet in the worst case but is smaller and faster on small sets.

* TokenStreams now set the position increment in end(), so we can handle trailing holes.

* IndexWriter no longer clones the given IndexWriterConfig.

Lucene 4.5 also includes numerous optimizations and bugfixes.

### Highlights of the Solr release include:

* Custom sharding support, including the ability to shard by field.

* DocValue improvements: single valued fields no longer require a default
  value, allowiing dynamicFields to contain doc values, as well as
  sortMissingFirst and sortMissingLast on docValue fields.

* Ability to store solr.xml in ZooKeeper.

* Multithreaded faceting.

* CloudSolrServer can now route updates directly to the appropriate shard
  leader.

Solr 4.5 also includes numerous optimizations and bugfixes.
