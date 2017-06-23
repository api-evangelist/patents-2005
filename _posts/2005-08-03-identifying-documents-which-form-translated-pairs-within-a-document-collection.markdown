---

title: Identifying documents which form translated pairs, within a document collection
abstract: A training system for text to text application. The training system finds groups of documents, and identifies automatically similar documents in the groups which are similar. The automatically identified documents can then be used for training of the text to text application. The comparison uses reduced size versions of the documents in order to minimize the amount of processing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07813918&OS=07813918&RS=07813918
owner: Language Weaver, Inc.
number: 07813918
owner_city: Los Angeles
owner_country: US
publication_date: 20050803
---
This invention was made with government support under Contract No. N66001 00 1 8914 awarded by the Space and Naval Warfare Systems Command. The U.S. government has certain rights in the claimed inventions.

Text to text applications include machine translation automated summarization question answering and other similar applications where a machine carries out the function of understanding some kind of input information and generating text. The input information is often text but more generally can be any kind of information that is received and understandable by the machine.

Conventional text to text applications use heterogeneous methods for implementing the generation phase. Machine translation often produces sentences using application specific decoders that are based on work that was conducted on speech recognition. Automated summarization produces abstracts using task specific strategies.

Machine translation systems rely on training that is carried out based on corresponding or parallel information that exists in both of two languages. The information in the two languages can be from many sources. Sometimes it is known that the contents of two documents represent the same information.

The internet is a source of information. Documents on the Internet are often available in multiple different languages. However it may be difficult to identify mutual translations within the many different web pages on the Internet. Comparing all documents within the document pool using conventional systems would require a number of computations that scales with the square of the number of document pairs.

For example each English language page can be compared with every known French language page to determine the best match. This naive system would take extreme computation times to identify the training pairs.

Philip Resnik has suggested a method which identifies parallel documents by producing pairs of similar URLs which are presumed to be in different languages. For example if one URL says En and another URL is similar but differs only by stating FR then these are presumed to be parallel URLs.

Not all Web documents are in this form and Resnik s system is quite specific to web pages which have that specific kinds of URLs.

The present application teaches a system that forms a similarity measure that returns a score given a document pair. Techniques are disclosed which scale n log n with the number of documents.

One aspect forms a reduced size version of the document that is associated with the document contents and compares that reduced size version with comparably reduced sized versions in other languages. The reduced size document can be a document fingerprint.

Another aspect compares the documents using a probabilistic shuffling technique where the documents and contents are mixed and then compared to some but not all information about other documents. The shuffling may be carried out numerous times in order to obtain a best match.

The general structure and techniques and more specific embodiments which can be used to effect different ways of carrying out the more general goals are described herein.

A processor is assumed to have access to various sources . The sources may be parallel corpora of multiple language information. Specifically the sources may include translation memories probabilistic and non probabilistic word and phrase based dictionaries glossaries Internet information parallel corpora in multiple languages non parallel corpora in multiple languages having similar subject matter and human created translations. The processor creates training data .

The present application teaches a system of identifying mutual translations within a collection of documents such as . The documents are assumed to be in first and second languages.

A first embodiment describes the first and second languages as being English and French. It should be understood however that any first and second languages could be used. The language information is used to train a machine based text to text system. That system can be machine translation automated summarization speech recognition or any other machine application.

Data from the Web can be gathered by focused crawling. Alternatively other data can be obtained. The data includes a collection of information in first and second languages that does not necessarily have any subject matter connection. This data is used as the input to the system.

The processing computer operates to find mutual translations according to the flowchart of . At each of the French language documents are translated into English using a rough machine translator. This rough translation is done quickly and makes an adequate but not perfect translation. The translation technique which is used at is optimized for speed not for accuracy. This translation produces two sets of documents in the same language here English. One of those sets of documents is the original English document called herein the native documents. The other set of documents is the translated documents.

At reduced size versions of the documents are created for both the native and translated documents. The reduced size version has parts that are associated with the document contents. The reduced size document can be a document fingerprint. The fingerprint has keys that relate to words and their placement in the dictionaries. In effect this summarizes concisely information about the words contained in the document.

Different techniques of forming fingerprints may be used and one specific technique is described herein with reference to . At n dictionaries are obtained. A dictionary can be any grouping of words which includes the words in the language of the documents. The dictionaries can be conventional dictionaries or any other collection of words. Each of the dictionaries will have different words in different orders. At the system identifies which word in the document appears first or at some specified location within each dictionary. The number of that word in the document is assigned to a key that corresponds to the dictionary at . Each dictionary will be different and therefore each dictionary will form a different key. Each of the keys will be associated with the document contents.

The keys collectively form a fingerprint. A typical system of this type may use 128 different dictionaries and hence the fingerprint shown in is formed of 128 different keys. Each document will form a unique set of keys and conversely the keys effectively form a signature that allows identification of the document. Any other type signature which identifies the document can alternatively be used. At each of the native and translated documents is compared to its neighboring document that is not to all documents in the database but only to specified neighboring documents. The comparison may use for example a fast Hamming matching. The comparison may only be to the left and right neighbors or may alternatively be to 2 5 left and right nearest neighbors or to some other number of neighbors. The Hamming distance is found at and represents how many pieces of the pair of fingerprints do not match.

Even a document and its identical translation would not match exactly because of imperfections in the translator for example. The Hamming distance indicates the amount by which the fingerprints do not match.

At a shuffle is carried out in which the order of the keys within the native and translated fingerprints are shuffled randomly. After shuffling the documents are sorted at according to fingerprints. The documents are again compared to their nearest neighbor s at . Flow continues until a desired match is obtained. The output is the closest neighbor at .

The shuffle operation uses statistical properties to find the nearest neighbor. For a database with 1 000 documents for example the shuffle can find the nearest neighbor after approximately 50 shuffles.

The SHUFFLE process is done so that the keys can be sorted in a way that brings similar items nearby so that they get compared.

However the ordering of the documents may be very different depending on the key order. A worst case shuffle for example may lead to the following key re ordering 

When documents are sorted according to their keys and according to this worst case scenario doc doc are likely to be very far apart. An example sorting might be 

In contrast a best case shuffle will put the like keys in agreement for example a best case shuffle might be 

Another embodiment is described with reference to the flowchart of . This embodiment does not require a rough translation but instead compares aspects of the documents that are in the document collection.

At each document in the collection is analyzed according to an assessment vector technique. The analysis may look for any category or feature within each document. For example the assess operation at may maintain a detection of the number of times that a specified word is used and keep counts of those multiple uses. The analyzed information is used to form vectors indicative of the documents. In this embodiment the vectors form the reduced versions.

The vectors can be native or may use a translation technique. For example a word frequency vector can be used for English documents while a modified word frequency vector can be used place the words from the French document into the English space.

At the vectors are compared and shuffled at using similar techniques to those in a previous embodiment.

According to exemplary embodiments a processor may determine reduced size versions of documents such as those that may be included in a database. A processor may also compare the reduced size versions to determine documents that represent similar information. Additionally a text to text application module may use documents that represent similar information to train a text to text application. The text to text application may be a machine translation system in some embodiments. Furthermore the text to text application may carry out a rough translation of documents to form a group of translated documents.

Although only a few embodiments have been disclosed in detail above other embodiments are possible and are intended to be encompassed within this specification. The specification describes specific examples to accomplish a more general goal that may be accomplished in other way. This disclosure is intended to be exemplary and the claims are intended to cover any modification or alternative which might be predictable to a person having ordinary skill in the art. For example the above techniques can be used with other sources of information other languages and other signature techniques.

Also only those claims which use the words means for are intended to be interpreted under 35 USC 112 sixth paragraph. Moreover no limitations from the specification are intended to be read into any claims unless those limitations are expressly included in the claims.

