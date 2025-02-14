# Biomedical Annotation Guidelines (Enhanced for Fine-Grained Classification with Syntactic/Lexical Cues)

These guidelines describe how to locate and categorize disease-related mentions in biomedical texts. The objective is not only to find where disease mentions occur but also to assign the correct category among four options:
- **SpecificDisease**
- **DiseaseClass**
- **CompositeMention**
- **Modifier**

All annotations are inserted directly into the text as tags.

---

## Annotation Tags

- `<category="SpecificDisease">…</category>` – For a single, well-defined disease entity or its abbreviation when used independently.
- `<category="DiseaseClass">…</category>` – For mentions that refer generically to a family or broad category of diseases.
- `<category="CompositeMention">…</category>` – For a contiguous phrase that contains two or more distinct disease names that must be kept together.
- `<category="Modifier">…</category>` – For disease-related terms that function as adjectives to modify another noun (e.g., a gene, protein, allele, mutation, kindred) rather than serving as the primary disease mention.

---

## I. Decision Tree for Category Assignment

1. **Identify the Mention Span:**  
   - Locate the text string that appears to denote a disease.

2. **Composite vs. Single Mention:**  
   - **If** the span includes two or more distinct disease names in one contiguous phrase (e.g., “Duchenne and Becker muscular dystrophy”), annotate it as `<category="CompositeMention">…</category>` and stop.
   - **Else,** proceed to the next step.

3. **Modifier Check (Syntactic & Lexical Cues):**  
   - **Examine the immediate context:**  
     - **If** the disease term is immediately adjacent (before or after) to a noun that suggests it is modifying another entity (e.g., “gene,” “protein,” “allele,” “mutation,” “kindred”), then label it as `<category="Modifier">…</category>`.
   - **Example:**  
     - “WD gene ATP7B” → `<category="Modifier">WD</category> gene ATP7B`
     - “HNPCC kindreds” → `<category="Modifier">HNPCC</category> kindreds`
   - **If not,** proceed to the next step.

4. **Broad Category vs. Specific Entity:**  
   - **If** the mention is generic or refers to a broad family of diseases (e.g., “autosomal recessive disease,” “neurodegenerative disorders”), annotate it as `<category="DiseaseClass">…</category>`.
   - **Else,** annotate it as `<category="SpecificDisease">…</category>`.

---

## II. Detailed Category Definitions & Examples

### 1. SpecificDisease
- **Definition:** A single, well-defined disease entity or its standard abbreviation when it stands alone.
- **Criteria:**  
  - The mention is not functioning as a modifier.
  - It does not refer to a broad or generic group.
- **Examples:**  
  - “Diastrophic dysplasia”  
  - “Huntington disease” and “HD” (when not immediately modifying another noun)  
  - “CT” when it denotes copper toxicosis on its own

### 2. DiseaseClass
- **Definition:** A term that refers to a broad family or generic category of diseases.
- **Criteria:**  
  - Often plural or generic descriptors (e.g., “cancers,” “neurodegenerative disorders”).
  - Lacks a specific clinical definition.
- **Examples:**  
  - “autosomal recessive disease”  
  - “familial cancers”

### 3. CompositeMention
- **Definition:** A contiguous text string that groups together multiple distinct disease names.
- **Criteria:**  
  - The grouping is necessary to preserve meaning.
  - Splitting the phrase would lose key context.
- **Examples:**  
  - “Duchenne and Becker muscular dystrophy”  
  - “colorectal, endometrial, and ovarian cancers”

### 4. Modifier
- **Definition:** A disease term that functions as an adjective modifying another noun.
- **Criteria:**  
  - Immediately adjacent to key lexical items (e.g., “gene,” “protein,” “allele,” “mutation,” “kindred”).
  - Serves to qualify another entity rather than stand alone.
- **Examples:**  
  - “WD gene ATP7B” → `<category="Modifier">WD</category> gene ATP7B`
  - “HNPCC kindreds” → `<category="Modifier">HNPCC</category> kindreds`
  - In “Patients with WD,” if no modifying noun follows, annotate “WD” as SpecificDisease.

---

## III. Core Rules & Additional Considerations

1. **Duplicate Mentions:**  
   - Annotate every occurrence of a disease mention, even if repeated in a sentence.

2. **Minimum Necessary Span:**  
   - Select only the shortest span that fully captures the disease concept, avoiding extra adjectives not integral to the name.

3. **Synonymous Mentions:**  
   - When both a long form and an abbreviation appear (e.g., “Huntington disease (HD)”), annotate both separately as SpecificDisease (unless context indicates one is a modifier).

4. **No Overlapping/Nested Annotations:**  
   - Avoid splitting or overlapping tags; if nested, choose the most complete and contextually appropriate mention.

5. **What Not to Annotate:**  
   - **Organism names** (unless explicitly tied to a disease)  
   - **Gender tokens** (unless indicating a distinct disease form)  
   - **Generic terms** (e.g., “disease,” “syndrome”) unless they are part of a recognized disease name  
   - **Biological process terms** (e.g., “tumorigenesis”)

---

## IV. Summary of Key Points

- **CompositeMention:** Use if multiple distinct diseases appear in one contiguous phrase.
- **Modifier:** Use if the disease term is immediately adjacent to a key lexical cue (e.g., "gene", "protein", "kindred").
- **DiseaseClass:** Use for generic or family-level disease descriptors.
- **SpecificDisease:** Use when the mention clearly identifies a single, well-defined disease.

---

## V. Additional Examples

1. **“We examined whether the WD gene ATP7B was also causative for CT.”**  
   - `<category="Modifier">WD</category> gene ATP7B`  
   - `<category="SpecificDisease">CT</category>`

2. **“autosomal recessive disease”**  
   - `<category="DiseaseClass">autosomal recessive disease</category>`

3. **“Duchenne and Becker muscular dystrophy”**  
   - `<category="CompositeMention">Duchenne and Becker muscular dystrophy</category>`

4. **“Patients with WD typically present with neurological symptoms.”**  
   - `<category="SpecificDisease">WD</category>`  
     (Here, "WD" stands alone without a modifying noun.)

5. **“Inherited spinocerebellar ataxia”**  
   - Typically `<category="SpecificDisease">Inherited spinocerebellar ataxia</category>`, unless context indicates a broad disease family.

---

By following these guidelines and the decision tree with explicit syntactic and lexical cues, annotators and models should achieve a more accurate and consistent classification of disease mentions.

# End of Guidelines
