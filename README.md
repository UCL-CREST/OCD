## OCD Framework: A Comparison of Code Similarity Analysers
### [Chaiyong Ragkhitwetsagul](https://cragkhit.github.io), [Jens Krinke](http://www0.cs.ucl.ac.uk/staff/j.krinke/index.html), [David Clark](http://www0.cs.ucl.ac.uk/staff/D.Clark/)
#### [CREST centre](http://crest.cs.ucl.ac.uk/), Department of Computer Science, University College London

Additional material to:

Chaiyong Ragkhitwetsagul, Jens Krinke, David Clark: A Comparison of Code Similarity Analysers. (Please email the authors for a copy.)

As an extension to:

Chaiyong Ragkhitwetsagul, Jens Krinke, David Clark: Similarity of Source Code in the Presence of Pervasive Modifications. 16th International Working Conference on Source Code Analysis and Manipulation (SCAM), Raleigh, NC, USA, October 2016.

### Abstract
Source code analysis to detect code cloning, code plagiarism, and code reuse suffers from the problem of code modifications. We are interested in two types of code modifications in this study: pervasive modifications, i.e. transformations that may have a global effect, and local modifications, i.e. code changes that are contained in a single method or code block. We evaluate 30 similarity detection techniques and tools using five experimental scenarios for Java source code. These are (1) pervasively modified code, created with tools for source code and bytecode obfuscation, and boiler-plate code, (2) source code normalisation through compilation and decompilation using different decompilers, (3) reuse of optimal configurations over different data sets, (4) tool evaluation using ranked-based measures, and (5) local+global code modifications. Our experimental results show that with the presence of pervasive modifications, some of the general textual similarity measures can offer similar performance to specialised code similarity tools, while in the presence of boiler-plate code, highly specialised source code similarity detection techniques and tools outperform textual similarity measures. Our study strongly validates the use of compilation/decompilation as a normalisation technique. Its use reduced false classifications to zero for three of the tools. Moreover, we demonstrate that optimal configurations are very sensitive to a specific data set. After directly applying optimal configurations derived from one data set to another, the tools perform poorly on the new data set. Code similarity analysers are thoroughly evaluated not only based on several well-known pair-based and query-based error measures but also on each specific type of pervasive code modification. This broad, thorough study is the largest in existence and potentially an invaluable guide for future users of similarity detection in source code.

### Contents
1. [The Experimental Framework](#the-experimental-framework)
2. [Tools and Techniques](#tools-and-techniques)
3. Scenario 1: Pervasive Modifications (data set)
4. Scenario 2: Decompilation (data set)
5. Scenario 3: Reused Boiler-Plate Code (data set)
6. Scenario 4: Ranked Results
7. Scenario 5: Local + Global Modifications (data set)
8. Results
9. Research Question 1 (Performance comparison)
10. Research Question 2 (Optimal Configurations)
11. Research Question 3 (Normalisation by Decompilation)
12. Research Question 4 (Reuse of Configurations)
13. Research Question 5 (Ranked Results)
14. Research Question 6 (Local + Global Code Modifications)

### The Experimental Framework

The general framework of our study as shown below consists of 5 main steps. In Step 1, we collect test data consisting of Java source code files. Next, the source files are transformed by applying pervasive modifications at source and bytecode level. In the third step, all original and transformed source files are normalised. A simple form of normalisation is pretty printing the source files which is used in similarity or clone detection. We also use decompilation. In Step 4, the similarity detection tools are executed pairwise against the set of all normalised files, producing similarity reports for every pair. In the last step, the similarity reports are analysed.

![Experimental Framework](https://github.com/UCL-CREST/ocd/blob/master/1.png)

### Tools and Techniques

Several tools and techniques were used in this study. These fall into three categories: obfuscators, decompilers, and detectors. The tool set included source and bytecode obfuscators, and two decompilers. The detectors cover a wide range of similarity measurement techniques and methods including plagiarism and clone detection, compression distance, string matching, and information retrieval. All tools are open source in order to expedite the repeatability of our experiments.

#### Obfuscators, Decompilers

Type	| Tool |	Link
------|------|------
Source code obfuscator	| Artifice	| [Download](https://www.tu-braunschweig.de/isf/research/artifice/index.html)
Bytecode obfuscator	    | ProGuard  |	[Download](http://proguard.sourceforge.net/)
Decompiler	            | Krakatau  |	[Download](https://github.com/Storyyeller/Krakatau)
Decompiler              | Procyon	  | [Download](https://bitbucket.org/mstrobel/procyon/wiki/Java%20Decompiler)

#### Similarity Detection Tools

| Tool/technique	| Similarity calculation |	Link |
|----------------|------------------------|------|
| Clone detectors |   |  |
| ccfx	| tokens and suffix tree matching	| [Download](http://www.ccfinder.net/) |
| deckard	| characteristic vectors of AST optimised by LSH | [Download](https://github.com/skyhover/Deckard) |
| iclones | tokens and generalised suffix tree	| [Download](http://www.softwareclones.org/iclones.php) |
| nicad	| TXL and string comparison (LCS)	| [Download](http://www.txl.ca/nicaddownload.html) |
| simian |	line-based string comparison	| [Download](http://www.harukizaemon.com/simian/) |
| Plagiarism detectors | | |
| jplag-java |	tokens, Karp Rabin matching, Greedy String Tiling	| [Download](https://jplag.ipd.kit.edu/) |
| jplag-text |	tokens, Karp Rabin matching, Greedy String Tiling | [Download](https://jplag.ipd.kit.edu/) |
| plaggie	| N/A (not disclosed) | [Download](https://www.cs.hut.fi/Software/Plaggie/) |
| sherlock |	digital signatures | [Download](http://sydney.edu.au/engineering/it/%20scilect/sherlock/) |
| simjava	| tokens and string alignment	| [Download](http://dickgrune.com/Programs/similarity_tester/) |
| simtext	| tokens and string alignment | [Download](http://dickgrune.com/Programs/similarity_tester/) |
| Compression | | |
| 7zncd	| NCD with 7z	| |
| bzip2ncd |	NCD with bzip2 | |
| gzipncd	| NCD with gzip |	|
| xzncd	| NCD with xz	| |
| icd		| ![ICD](https://github.com/UCL-CREST/ocd/blob/master/2.png) | |
| ncd	| ncd tool with bzlib & zlib | [Download](http://complearn.org/ncd.html) |
| Others | | |
| bsdiff | ![bsdiff](https://github.com/UCL-CREST/ocd/blob/master/3.png) | |
| diff | ![diff](https://github.com/UCL-CREST/ocd/blob/master/4.png) | |
| py-difflib | Gestalt pattern matching	| [Download](https://docs.python.org/2/library/difflib.html) |
| py-fuzzywuzzy |	fuzzy string matching	| [Download](https://github.com/seatgeek/fuzzywuzzy) |
| py-jellyfish | approximate and phonetic matching of strings py-ngram fuzzy search based using n-gram | [Download](https://github.com/jamesturk/jellyfish) |
| py-sklearn | cosine similarity from machine learning library | [Download](http://scikit-learn.org/stable/) |
