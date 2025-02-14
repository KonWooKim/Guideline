# Biomedical Annotation Guidelines (Classification-Focused)

These guidelines describe how to **locate** and **categorize** disease-related mentions in biomedical texts. The primary objective is to **capture disease names accurately** (where they occur) and **assign them to the correct category**—`SpecificDisease`, `DiseaseClass`, `CompositeMention`, or `Modifier`.

---

## Annotation Tags

- `<category="SpecificDisease">…</category>`  
- `<category="DiseaseClass">…</category>`  
- `<category="CompositeMention">…</category>`  
- `<category="Modifier">…</category>`

Use one of these four tags for each disease-related mention.

---

## I. Decision Tree for Category Selection

1. **Identify the Disease Mention Span**  
   - First, locate each disease mention or abbreviation.

2. **Check for Composite vs. Single Mention**  
   - **If** the contiguous text string contains multiple diseases combined (e.g., “Duchenne and Becker muscular dystrophy”), annotate the entire phrase as `<category="CompositeMention">...</category>` and **stop**.  
   - **Else** (it’s a single disease mention), continue to the next step.

3. **Check if the Mention is Used as a Modifier**  
   - **If** the disease term modifies another entity (gene, protein, family, etc.), use `<category="Modifier">...</category>`.  
   - **Else**, go to the next step.

4. **Check if it’s a Broad Family vs. Specific Disease**  
   - **If** it refers to a broad category/family of diseases, annotate as `<category="DiseaseClass">...</category>`.  
   - **Otherwise**, it’s a `<category="SpecificDisease">...</category>`.

---

## II. Category Definitions

### 1. SpecificDisease
A **single, well-defined disease** (or its abbreviation) that is **not** modifying another entity.

- **Examples**  
  - “Diastrophic dysplasia”  
  - “Huntington disease” / “HD”  
  - “Wilson disease” (WD) if it stands alone in context

### 2. DiseaseClass
A **broad category** or **family** of diseases.

- **Examples**  
  - “autosomal recessive disease” (generic group)  
  - “neurodegenerative disorders”  
  - “familial cancers” (if used generically)

### 3. CompositeMention
A **single, contiguous phrase** that includes two or more distinct disease entities.

- **Examples**  
  - “Duchenne and Becker muscular dystrophy”  
  - “colorectal, endometrial, and ovarian cancers”

### 4. Modifier
A disease term used **adjectivally** to describe another noun (gene, protein, etc.).

- **Examples**  
  - “WD gene ATP7B” → `<category="Modifier">WD</category>`  
  - “HNPCC kindreds” → `<category="Modifier">HNPCC</category>`

---

## III. Core Annotation Rules

1. **Duplicate Mentions**  
   - Mark **every** occurrence of a disease mention, even if it appears multiple times.

2. **Minimum Necessary Span**  
   - Include all tokens needed for the most specific form of the disease, excluding unnecessary words.

3. **Synonymous Mentions**  
   - If both a long form and an abbreviation appear, annotate both.  
   - Example:  
     ```html
     <category="SpecificDisease">Huntington disease</category>
     <category="SpecificDisease">HD</category>
     ```

4. **No Overlapping/Nested Mentions**  
   - Avoid overlapping tags. If in doubt, choose the mention that represents the most specific or complete disease form.

5. **What Not to Annotate**  
   - **Organism names** (unless specifically referencing a disease caused by that organism)  
   - **Gender tokens** (“male,” “female”) unless indicating a unique disease form  
   - **Generic terms** (“disease,” “syndrome,” “deficiency,” etc.) unless used precisely as part of a recognized disease name  
   - **Biological processes** (“tumorigenesis,” “cancerogenesis”)  

---

## IV. Additional Examples

1. **“We examined whether the WD gene ATP7B was also causative for CT.”**  
   - `<category="Modifier">WD</category> gene ATP7B`  
   - `<category="SpecificDisease">CT</category>`

2. **“autosomal recessive disease”**  
   - `<category="DiseaseClass">autosomal recessive disease</category>`

3. **“Duchenne and Becker muscular dystrophy”**  
   - `<category="CompositeMention">Duchenne and Becker muscular dystrophy</category>`

4. **“Patients with WD typically present with neurological symptoms.”**  
   - `<category="SpecificDisease">WD</category>` (not modifying a gene/protein, so it’s a standalone disease mention)

5. **“Inherited spinocerebellar ataxia”**  
   - Typically `<category="SpecificDisease">Inherited spinocerebellar ataxia</category>`, unless the context indicates it’s a broad class.

---

## V. Improving Model Performance

1. **Short Prompts with a Decision Tree**  
   - Provide a concise bullet list or flowchart so the model can quickly decide among the four categories.

2. **Additional Edge-Case Examples**  
   - Especially around “Modifier” vs. “SpecificDisease” or “DiseaseClass” vs. “SpecificDisease.”

3. **Post-Processing Validation**  
   - Optionally, run a script to detect suspicious cases (e.g., a mention labeled as “Modifier” but not adjacent to a noun like “gene” or “protein”).

4. **Iterative Feedback**  
   - Evaluate model output, identify systematic errors, and refine examples or rules accordingly.

---

# End of Guidelines
