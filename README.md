What to Annotate:

Annotate all Specific Disease mentions

A textual string referring to a disease name may refer to a Specific Disease, or a Disease Class. Disease mentions that could be described as a family of many Specific Diseases were annotated with an annotation category called Disease Class. The annotation category Specific Disease was used for those mentions which could be linked to one specific definition that does not include further categorization.

e.g. Diastrophic dysplasia is an autosomal recessive disease characterized by short stature, very short limbs and joint problems that restrict mobility.

Annotate: "Diastrophic dysplasia" as Specific Disease category and "autosomal recessive disease" as Disease Class category

Annotate contiguous text strings.

A textual string may refer to two or more separate disease mentions. Such mentions are annotated with the Composite Mention category.

e.g. The text phrase "Duchenne and Becker muscular dystrophy" refers to two separate diseases. If this phrase is separated into two strings: "Duchenne" and "Becker muscular dystrophy", it results in information loss, because the word "Duchenne" on its own is not a disease mention.

Annotate disease mentions that are used as Modifiers for other concepts

A textual string may refer to a disease name, but it may modify a noun phrase, or not be a noun phrase and this is better expressed with the Modifier annotation category.

e.g.: Although this mutation was initially detected in four of 33 colorectal cancer families analysed from eastern England, more extensive analysis has reduced the frequency to four of 52 English HNPCC kindreds analysed.
Annotate: "colorectal cancer" as Modifier category and "HNPCC" as Modifier category.

Annotate duplicate mentions.

For each sentence in the PubMed abstract and title, the locations of all disease mentions are marked, including duplicates within the same sentence.


Annotate minimum necessary span of text.

The minimum span of text necessary to include all the tokens expressing the most specific form of the disease is preferred.

e.g., in the case of "insulin-dependent diabetes mellitus", the disease mention including the whole phrase was preferred over its substrings such as "diabetes mellitus" or "diabetes".


Annotate all synonymous mentions.

Abbreviation definitions such as "Huntington disease" ("HD") are separated into two annotated mentions.

What NOT to Annotate:

Do not annotate organism names.

Organism names such as "human" were excluded from the preferred mention. Viruses, bacteria, and other organism names were not annotated unless it was clear from the context that the disease caused by these organisms is discussed.

e.g. Studies of biopsied tissue for the presence of Epstein-Barr virus and cytomegalovirus were negative.

In this case: "Epstein-Barr virus" and "cytomegalovirus" are annotated as Specific Disease category.


Do not annotate gender.

Tokens such as "male" and "female" were only included if they specifically identified a new form of the disease,

e.g. "male breast cancer".


Do not annotate overlapping mentions.

For example, the phrase "von Hippel-Lindau (VHL) disease" was annotated as one single disease mention, Specific Disease category.


Do not annotate general terms.

Very general terms such as: disease, syndrome, deficiency, complications, abnormalities, etc. were excluded. However, the terms cancer and tumor were retained.


Do not annotate references to biological processes.

e.g. Terms corresponding to biological processes such as "tumorigenesis" or "cancerogenesis".


Do not annotate disease mentions interrupted by nested mentions.

Basically, do not break the contiguous text rule.

e.g. WT1 dysfunction is implicated in both neoplastic (Wilms tumor, mesothelioma, leukemia, and breast cancer) and nonneoplastic (glomerulosclerosis) disease.

In this example, the list of all disease mentions includes: "neoplastic disease" and "nonneoplastic disease" in addition to"Wilms tumor", "mesothelioma", "leukemia", "breast cancer" and "glomerulosclerosis". However, they were not annotated in our corpus, because other tokens break up the phrases.

Examples:

"Insulin-dependent diabetes mellitus", Specific Disease, prefer the whole string


CDH1 mutations predispose to early onset "colorectal cancer"

"early onset" may or may not be part of the disease mention, depends on 1. If ether is a UMLS concept specifying this as a separate form of disease, and 2. If the annotator believes it should be included.


Human "X-linked recessive disorder"


Her fresh serum lacked complement-mediated bactericidal activity against Neisseria gonorrhoeae.


"Huntington disease" ("HD"), the long form and the short form constitute two separate mentions


This report represents the first cases of "C7 deficiency" associated with infectious complications

"infectious complications" is too general a term; C7 deficiency however is a Specific Disease.


"colorectal, endometrial, and ovarian cancers" is considered one Composite Mention of several Specific Diseases.


WT1 dysfunction is implicated in both neoplastic ( "Wilms tumor" , "mesothelioma" , "leukemias" , and "breast cancer" ) and nonneoplastic ( "glomerulosclerosis" ) disease.

If we list all disease mentions in this sentence we have the following: Neoplastic disease, nonneoplastic disease, wilms tumor, mesothelioma, leukemias, breast cancer, glomerulosclerosis. However, "neoplastic disease" or "nonneoplastic disease" are not annotated because these mentions are intercepted with other tokens.


Tumorigenesis and cancerogenesis are not annotated as diseases in this corpus. These terms correspond to the process by which normal cells are transformed into cancer cells.


"autosomal recessive disease" refers to a whole family of diseases which can be passed down through families because of their genetic characteristics " Disease Class category


Large phenotypic variability has been observed, with convulsive disorders, motor retardation and mental retardation being the most abundant manifestations.

"convulsive disorders", "motor retardation" and "mental retardation" are examples of the grey area terms which may be classified as disease mentions, but do not correspond to one Specific Disease, therefore they are annotated as Disease Class category


Borjeson-Forssman-Lehmann syndrome ( BFLS ) is a syndromal X-linked mental retardation.

In this case, "X-linked mental retardation syndrome" is a family of diseases, and "Borjeson-Forssman-Lehmann syndrome" is a Specific Disease of that family.


Acute meningococcal pericarditis " Constitutes a disease mention and, exists as a separate concept in UMLS, however

Acute Neisseria infection " May or may not include "acute" in the mention name.


Classical galactosemia " Includes "classical", because it corresponds to a particular form of the disease.


Inherited spinocerebellar ataxia " May or may not include "inherited", depends on annotator
Adenomatous polyps of the colon and rectum, - Composite Mention
Fibroepithelial or epithelial hyperplasias, - Composite Mention


Stage II or stage III colorectal cancer " Composite Mention

How annotators used the annotation tool:
For each annotator:

Please:

Go to annotation webpage


Follow instructions to select your domain


Work one annotation set at a time


For each PubMed abstract:

Select PMID to open the editor page. See Figure for an illustration.

The editor page provides the following information:

At the top of the page the PMID links to PubMed record.

Inside the editor there are three fields: PMID, TITLE and ABSTRACT.

Above the editor window are listed the annotation categories: Specific Disease (highlighted in yellow), Disease Class (green), Composite Mention (blue), or Modifier (purple)

At the end of the editor is the "Submit" button.


Please annotate the title and the abstract portion of the text.

To annotate a new mention: Select the string to be annotated by holding the mouse down and highlighting the whole selection, then click on the appropriate category label listed above the editor window.

To delete a previously annotated mention: Select the string to be removed from the annotations list by holding the mouse down and highlighting the whole selection, then click on "Clear" label above the editor window.

After the abstract has been processed, press the "Submit" button found just below the editor window.

To retrieve the last saved version of your annotations click on "Last Saved" button.

To undo all your annotations about this particular document and start anew with the pre-annotated version click on "Clear ALL, start from the beginning"

The pre-annotated version considers all mentions as "Specific Disease" category. To change the category, hold the mouse button to highlight the text and click on the appropriate category label above the editor window.

To change the span of a previously annotated mention, hold the mouse button to highlight the desired text and click on the appropriate category label above the editor window.
