# Biomedical Annotation Guidelines (Refined)

These guidelines describe how to annotate disease-related mentions in biomedical texts. The goal is to capture disease names, related modifiers, and composite mentions while ensuring that only the minimum necessary text is marked. All annotations are inserted directly into the text as tags.

---

## Annotation Tags

- `<category="SpecificDisease">…</category>` – For specific, well-defined disease entities.
- `<category="DiseaseClass">…</category>` – For mentions that refer to a family or group of diseases.
- `<category="CompositeMention">…</category>` – For phrases that include two or more disease mentions that must be kept together.
- `<category="Modifier">…</category>` – For disease terms used to modify another noun (e.g., gene or protein names) rather than being the primary disease mention.

---

## I. What to Annotate

### 1. Specific Disease Mentions
- **Specific Disease:**  
  Annotate any disease name that clearly refers to a single, defined disease entity.
  - **Example:**  
    - **Input:** “Diastrophic dysplasia is an autosomal recessive disease…”  
    - **Annotation:**  
      - `<category="SpecificDisease">Diastrophic dysplasia</category>`

- **Disease Class:**  
  When the term refers to a family of related diseases, annotate it as a disease class.
  - **Example:**  
    - **Input:** “autosomal recessive disease” (when used in a generic sense)  
    - **Annotation:**  
      - `<category="DiseaseClass">autosomal recessive disease</category>`

---

### 2. Contiguous Text Strings (Composite Mentions)
- **Composite Mention:**  
  When a contiguous phrase refers to multiple disease mentions that should not be split, annotate the entire phrase as a composite mention.
  - **Example:**  
    - **Input:** “Duchenne and Becker muscular dystrophy”  
    - **Annotation:**  
      - `<category="CompositeMention">Duchenne and Becker muscular dystrophy</category>`

---

### 3. Disease Mentions Used as Modifiers
- **Modifier:**  
  If a disease term is used to modify another entity (for example, a gene or protein name), annotate it as a modifier rather than as a standalone disease mention.
  - **Guidelines:**  
    - **Decision Point:** Examine the syntactic context:
      - If the term functions as an adjective (e.g., “WD gene ATP7B”), mark it as a modifier.
      - If the term stands alone referring to a disease entity (e.g., “Patients with WD”), annotate it as a specific disease.
  - **Example:**  
    - **Input:** “WD gene ATP7B”  
    - **Annotation:**  
      - `<category="Modifier">WD</category> gene ATP7B`

---

### 4. Duplicate Mentions
- **Duplicate Mentions:**  
  Annotate every occurrence of a disease mention in a sentence—even if it appears multiple times.
  - **Example:**  
    - **Input:** “Diabetes is common. Diabetes prevalence is increasing.”  
    - **Annotation:**  
      - Both occurrences of “Diabetes” should be annotated accordingly.

---

### 5. Minimum Necessary Span
- **Minimum Span:**  
  Annotate only the smallest span of text that fully conveys the disease concept.
  - **Guidelines:**  
    - Avoid including extraneous adjectives unless they are integral to the disease name.
  - **Example:**  
    - **Input:** “insulin-dependent diabetes mellitus”  
    - **Annotation:**  
      - `<category="SpecificDisease">insulin-dependent diabetes mellitus</category>`  
    - **Note:** Do not annotate just “diabetes mellitus” or “diabetes” if the full concept is required.

---

### 6. Synonymous Mentions
- **Synonymous Mentions:**  
  If both a long form and an abbreviation of a disease appear, annotate each as a separate mention.
  - **Example:**  
    - **Input:** “Huntington disease (HD)”  
    - **Annotation:**  
      - `<category="SpecificDisease">Huntington disease</category>`  
      - `<category="SpecificDisease">HD</category>`

---

## II. What Not to Annotate

1. **Organism Names:**  
   - Do not annotate names like “human” unless the text clearly refers to the disease caused by that organism.  
   - **Example:** “Epstein-Barr virus” should only be annotated if it is explicitly tied to a disease context.

2. **Gender Tokens:**  
   - Do not annotate tokens such as “male” or “female” unless they specifically indicate a unique disease form.  
   - **Example:** In “male breast cancer,” do not annotate “male” separately.

3. **Overlapping Mentions:**  
   - Do not break overlapping disease mentions into multiple annotations.  
   - **Example:** “von Hippel-Lindau (VHL) disease” should be annotated as one mention.

4. **General Terms:**  
   - Do not annotate overly generic terms (e.g., “disease,” “syndrome,” “deficiency,” “complications”) unless used to define a specific concept.  
   - **Note:** Terms such as “cancer” and “tumor” can be annotated if used precisely.

5. **Biological Processes:**  
   - Do not annotate words that refer to biological processes (e.g., “tumorigenesis,” “cancerogenesis”).

6. **Interrupted Phrases:**  
   - Do not annotate if the phrase is broken by nested mentions that prevent a contiguous disease mention.  
   - **Example:** In “WT1 dysfunction is implicated in both neoplastic (Wilms tumor, mesothelioma, leukemia, and breast cancer) and nonneoplastic (glomerulosclerosis) disease,” do not annotate “neoplastic disease” or “nonneoplastic disease” separately.

---

## III. Additional Examples

1. **“Insulin-dependent diabetes mellitus”**  
   - **Annotation:**  
     ```html
     <category="SpecificDisease">insulin-dependent diabetes mellitus</category>
     ```

2. **Modifier vs. Specific Disease Example:**  
   - **Input:** “We examined whether the WD gene ATP7B was also causative for CT...”  
   - **Annotation:**  
     - `<category="Modifier">WD</category>` (since it modifies “gene ATP7B”)  
     - `<category="SpecificDisease">CT</category>` (if CT refers to a disease entity such as copper toxicosis)

3. **Synonymous Mentions:**  
   - **Input:** “Huntington disease (HD)”  
   - **Annotation:**  
     ```html
     <category="SpecificDisease">Huntington disease</category>
     <category="SpecificDisease">HD</category>
     ```

4. **Composite Mention:**  
   - **Input:** “colorectal, endometrial, and ovarian cancers”  
   - **Annotation:**  
     ```html
     <category="CompositeMention">colorectal, endometrial, and ovarian cancers</category>
     ```

5. **Overlapping Example:**  
   - **Input:** “von Hippel-Lindau (VHL) disease”  
   - **Annotation:**  
     ```html
     <category="SpecificDisease">von Hippel-Lindau (VHL) disease</category>
     ```

---

## Summary of Key Refinements

- **Modifiers vs. Specific Disease:**  
  Clearly differentiate when a term is used as a modifier (e.g., “WD gene”) versus when it stands alone as a disease name. Use contextual clues (such as adjacent words like “gene” or “protein”) to decide.

- **Minimum Span:**  
  Annotate the smallest necessary string that still conveys the full disease concept, avoiding over-annotation of adjacent non-essential words.

- **Composite Mentions and Synonyms:**  
  Preserve information by marking composite mentions in one tag and by annotating both the long form and abbreviation when provided.

- **Consistency and Non-Overlap:**  
  Avoid overlapping or nested annotations by ensuring that each annotation captures a distinct, contiguous disease mention.

---

By following these refined guidelines, annotators (and models trained on these guidelines) should achieve a higher level of consistency and accuracy in distinguishing between specific disease mentions, modifiers, disease classes, and composite mentions.
