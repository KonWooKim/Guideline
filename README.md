# Biomedical Annotation Guidelines

## What to Annotate

### 1. Annotate all **Specific Disease** mentions
A textual string referring to a disease name may refer to a **Specific Disease** or a **Disease Class**.  
- **Disease Class**: Mentions that could be described as a family of multiple specific diseases.  
- **Specific Disease**: Mentions that can be linked to one specific definition that does not include further categorization.

**Example**  
> Diastrophic dysplasia is an autosomal recessive disease characterized by short stature, very short limbs and joint problems that restrict mobility.

- **Annotate**:  
  - “Diastrophic dysplasia” as **Specific Disease**  
  - “autosomal recessive disease” as **Disease Class**

---

### 2. Annotate **contiguous text strings**
A textual string may refer to two or more separate disease mentions. Such mentions are annotated with the **Composite Mention** category.

**Example**  
> The text phrase “Duchenne and Becker muscular dystrophy” refers to two separate diseases. If this phrase is separated into two strings: “Duchenne” and “Becker muscular dystrophy,” it results in information loss, because the word “Duchenne” on its own is not a disease mention.

---

### 3. Annotate disease mentions that are used as **Modifiers** for other concepts
A textual string may refer to a disease name, but it may modify a noun phrase (or may not be a noun phrase itself). In such cases, annotate using the **Modifier** category.

**Example**  
> Although this mutation was initially detected in four of 33 colorectal cancer families analysed from eastern England, more extensive analysis has reduced the frequency to four of 52 English HNPCC kindreds analysed.

- **Annotate**:  
  - “colorectal cancer” as **Modifier**  
  - “HNPCC” as **Modifier**

---

### 4. Annotate **duplicate mentions**
For each sentence in the PubMed abstract and title, the locations of all disease mentions are marked, including duplicates within the same sentence.

---

### 5. Annotate **minimum necessary span of text**
Use the smallest span necessary to include all tokens expressing the most specific form of the disease.

**Example**  
> In the case of “insulin-dependent diabetes mellitus,” the disease mention including the whole phrase was preferred over its substrings such as “diabetes mellitus” or “diabetes.”

---

### 6. Annotate all **synonymous mentions**
Abbreviation definitions such as “Huntington disease” (“HD”) are separated into two annotated mentions (one for the long form, one for the abbreviation).

---

## What NOT to Annotate

1. **Do not annotate organism names**  
   - Organism names such as “human” were excluded from the preferred mention.  
   - Viruses, bacteria, and other organism names were not annotated **unless** it was clear that the disease caused by these organisms is being discussed.  
   - **Example**  
     > Studies of biopsied tissue for the presence of Epstein-Barr virus and cytomegalovirus were negative.  
     
     In this case: “Epstein-Barr virus” and “cytomegalovirus” are annotated as **Specific Disease** category **only** if the context clearly indicates the diseases they cause, otherwise not.

2. **Do not annotate gender**  
   - Tokens such as “male” and “female” were only included if they specifically identified a new form of the disease.  
   - **Example**  
     > “male breast cancer”

3. **Do not annotate overlapping mentions**  
   - **Example**: The phrase “von Hippel-Lindau (VHL) disease” is annotated as **one single disease mention** (Specific Disease category).

4. **Do not annotate general terms**  
   - Very general terms such as “disease,” “syndrome,” “deficiency,” “complications,” “abnormalities,” etc. were excluded.  
   - However, the terms “cancer” and “tumor” were retained.

5. **Do not annotate references to **biological processes**  
   - e.g. Terms corresponding to biological processes such as “tumorigenesis” or “cancerogenesis.”

6. **Do not annotate disease mentions interrupted by nested mentions**  
   - Essentially, do not break the contiguous text rule.  
   - **Example**  
     > WT1 dysfunction is implicated in both neoplastic (Wilms tumor, mesothelioma, leukemia, and breast cancer) and nonneoplastic (glomerulosclerosis) disease.  
     
     Here, the mentions “neoplastic disease” and “nonneoplastic disease” are not annotated because other tokens break up these phrases.

---

## Examples

1. **“Insulin-dependent diabetes mellitus”**  
   - **Specific Disease**  
   - Prefer the whole string.

2. **CDH1 mutations predispose to early onset “colorectal cancer.”**  
   - “early onset” may or may not be part of the disease mention, depending on:  
     1. If there is a UMLS concept specifying this as a separate form of disease  
     2. If the annotator believes it should be included

3. **Human “X-linked recessive disorder”**

4. **Her fresh serum lacked complement-mediated bactericidal activity against Neisseria gonorrhoeae.**

5. **“Huntington disease” (“HD”)**  
   - The long form and the short form constitute two separate mentions.

6. **C7 deficiency**  
   - “This report represents the first cases of C7 deficiency associated with infectious complications.”  
   - “infectious complications” is too general a term; C7 deficiency is a **Specific Disease**.

7. **“colorectal, endometrial, and ovarian cancers”**  
   - Considered one **Composite Mention** of several Specific Diseases.

8. **WT1 dysfunction is implicated in both neoplastic (“Wilms tumor,” “mesothelioma,” “leukemias,” and “breast cancer”) and nonneoplastic (“glomerulosclerosis”) disease.**  
   - Potential disease mentions include: “neoplastic disease,” “nonneoplastic disease,” “Wilms tumor,” “mesothelioma,” “leukemias,” “breast cancer,” and “glomerulosclerosis.”  
   - “neoplastic disease” and “nonneoplastic disease” are **not** annotated because these phrases are interrupted by nested mentions.

9. **Tumorigenesis and cancerogenesis**  
   - These refer to processes, not diseases.

10. **“autosomal recessive disease”**  
    - Refers to a family of diseases that can be passed down genetically → **Disease Class** category.

11. **Large phenotypic variability with “convulsive disorders,” “motor retardation,” and “mental retardation.”**  
    - These are “grey area” terms: they may not correspond to a single **Specific Disease**, so they are annotated as **Disease Class** category if appropriate.

12. **Borjeson-Forssman-Lehmann syndrome (BFLS) is a syndromal X-linked mental retardation.**  
    - “Borjeson-Forssman-Lehmann syndrome” = **Specific Disease**  
    - “X-linked mental retardation syndrome” = a family of diseases (i.e., **Disease Class**)

13. **Acute meningococcal pericarditis**  
    - Exists as a separate concept in UMLS.

14. **Acute Neisseria infection**  
    - May or may not include “acute” depending on context.

15. **Classical galactosemia**  
    - Includes “classical” because it corresponds to a particular form of the disease.

16. **Inherited spinocerebellar ataxia**  
    - May or may not include “inherited,” depending on the annotator.

17. **“Adenomatous polyps of the colon and rectum”**  
    - **Composite Mention**

18. **Fibroepithelial or epithelial hyperplasias**  
    - **Composite Mention**

19. **Stage II or stage III colorectal cancer**  
    - **Composite Mention**

---
