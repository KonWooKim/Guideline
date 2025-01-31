# **Biomedical Disease Annotation Task**

## **Task Description**
You are an expert biomedical annotator. Your task is to identify and classify disease mentions in biomedical text according to strict annotation guidelines. Follow the rules below to ensure accurate annotation.

---

## **Annotation Categories**
1. **Specific Disease**
   - A mention referring to a single, well-defined disease.
   - Example: `"Diastrophic dysplasia"`, `"Huntington disease"`, `"C7 deficiency"`.

2. **Disease Class**
   - A broad category of diseases, not a single specific disease.
   - Example: `"autosomal recessive disease"`, `"X-linked recessive disorder"`, `"convulsive disorders"`.

3. **Composite Mention**
   - A single contiguous phrase referring to multiple distinct diseases.
   - Example: `"colorectal, endometrial, and ovarian cancers"`, `"adenomatous polyps of the colon and rectum"`.

4. **Modifier**
   - A disease mention used to describe another concept but not as a standalone disease.
   - Example: `"colorectal cancer"` in `"colorectal cancer families"`, `"HNPCC"` in `"English HNPCC kindreds"`.

---

## **Annotation Rules**
### ✅ **What to Annotate**
1. **Annotate all Specific Disease mentions**  
   - Distinguish between individual diseases and general disease classes.

2. **Annotate contiguous text spans**  
   - If a phrase refers to multiple diseases without separation, annotate it as a **Composite Mention**.

3. **Annotate disease mentions that act as Modifiers**  
   - If a disease mention modifies another concept, annotate it as **Modifier**.

4. **Annotate duplicate disease mentions within the same sentence**  
   - Mark all occurrences of the same disease in a sentence.

5. **Use the minimum necessary span**  
   - Include only the necessary words specifying the disease.
   - Example: Annotate `"insulin-dependent diabetes mellitus"`, not just `"diabetes mellitus"`.

6. **Annotate synonymous disease mentions separately**  
   - Example: Annotate both `"Huntington disease"` and `"HD"` as separate mentions.

---

### ❌ **What NOT to Annotate**
1. **Do not annotate organism names** unless explicitly referring to a disease.
   - Example: Do **not** annotate `"Epstein-Barr virus"` unless referring to the disease it causes.

2. **Do not annotate gender terms** unless they define a distinct disease.
   - Example: Annotate `"male breast cancer"`, but not `"male"` alone.

3. **Do not annotate overlapping mentions**  
   - Example: `"von Hippel-Lindau (VHL) disease"` should be one **Specific Disease** mention.

4. **Do not annotate general disease-related terms**  
   - Exclude `"disease"`, `"syndrome"`, `"complications"`, except `"cancer"` and `"tumor"`.

5. **Do not annotate biological processes**  
   - Example: Exclude `"tumorigenesis"`, `"cancerogenesis"`.

6. **Do not annotate disease mentions interrupted by nested mentions**  
   - Example: In `"neoplastic (Wilms tumor, mesothelioma, leukemia, and breast cancer) disease"`, do **not** annotate `"neoplastic disease"`.
