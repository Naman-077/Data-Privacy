
# Practical 5: Applying Data Anonymization Techniques to a Real-World Dataset

## Aim

To understand and apply different data anonymization techniques, including **data masking, generalization, k-anonymity, and differential privacy**, on a sample real-world-style dataset while maintaining a balance between privacy protection and data usefulness.

---

## 1. Introduction

Modern organizations collect large amounts of information about users, customers, students, patients, and employees. Such datasets may contain information that can directly or indirectly identify an individual.

Examples include:

- Name
- Email address
- Phone number
- Age
- Location
- IP address
- Salary
- Medical information
- Educational information

Before such data is shared for research, analysis, or machine learning, privacy-preserving techniques can be applied.

**Data anonymization** refers to modifying data so that identifying a particular individual becomes more difficult while retaining useful information for analysis.

Consider the following original record:

| Name | Age | City | Gender | Score |
|---|---:|---|---|---:|
| Aarav Sharma | 21 | Delhi | Male | 87 |

After anonymization:

| Name | Age Group | Region | Gender | Score |
|---|---|---|---|---:|
| [Removed] | 20–25 | North India | Male | 87 |

The second version provides useful statistical information without exposing the person's name or exact location.

---

# 2. Types of Data Used in Anonymization

Data fields can be classified according to their privacy risk.

### Direct Identifiers

These can identify an individual directly.

Examples:

- Name
- Email
- Phone number
- Aadhaar number
- Student ID

These are generally removed or masked.

### Quasi-Identifiers

These may not identify someone individually but can identify them when combined with other information.

Examples:

- Age
- Gender
- PIN code
- City
- Date of birth

These fields are often generalized.

### Sensitive Attributes

These contain information that should be protected.

Examples:

- Salary
- Medical condition
- Examination result
- Financial information

---

# 3. Sample Dataset

For this practical, a fictional student-performance dataset is used.

### Original Dataset

| Student Name | Age | City | Gender | Course | Score |
|---|---:|---|---|---|---:|
| Aarav | 21 | Delhi | M | B.Sc CS | 86 |
| Riya | 22 | Delhi | F | B.Sc CS | 91 |
| Karan | 21 | Noida | M | B.Sc CS | 78 |
| Simran | 23 | Gurgaon | F | BCA | 88 |
| Aditya | 22 | Ghaziabad | M | BCA | 75 |
| Neha | 21 | Delhi | F | BCA | 84 |
| Rahul | 24 | Noida | M | B.Sc CS | 72 |
| Priya | 23 | Gurgaon | F | B.Sc CS | 95 |

The **Student Name** is a direct identifier, while **Age, City, Gender, and Course** can act as quasi-identifiers.

---

# 4. Technique 1: Data Masking

Data masking hides sensitive information while keeping the structure of the dataset intact.

For example:

| Original Email | Masked Email |
|---|---|
| aarav@gmail.com | a***@gmail.com |
| riya@gmail.com | r***@gmail.com |

Similarly, a phone number such as:

```text
9876543210
```

can be displayed as:

```text
XXXXXX3210
```

### Purpose

Masking is useful when users need to see part of the information but should not have access to the complete value.

### Applications

- Banking systems
- Customer databases
- Hospital systems
- Employee records
- E-commerce platforms

---

# 5. Technique 2: Suppression

Suppression removes information that is unnecessary for the intended analysis.

For example, if the objective is to study examination performance, the student's name may not be required.

### Before Suppression

| Student Name | Age | City | Score |
|---|---:|---|---:|
| Aarav | 21 | Delhi | 86 |
| Riya | 22 | Delhi | 91 |

### After Suppression

| Age | City | Score |
|---:|---|---:|
| 21 | Delhi | 86 |
| 22 | Delhi | 91 |

The direct identifier has been removed.

---

# 6. Technique 3: Generalization

Generalization replaces precise information with a broader category.

For example:

```text
Age: 21
       ↓
Age Group: 20–25
```

Similarly:

```text
Delhi
Noida
Gurgaon
Ghaziabad
       ↓
NCR Region
```

### Transformed Dataset

| Age Group | Region | Gender | Course | Score |
|---|---|---|---|---:|
| 20–25 | Delhi NCR | M | B.Sc CS | 86 |
| 20–25 | Delhi NCR | F | B.Sc CS | 91 |
| 20–25 | Delhi NCR | M | B.Sc CS | 78 |
| 20–25 | Delhi NCR | F | BCA | 88 |
| 20–25 | Delhi NCR | M | BCA | 75 |
| 20–25 | Delhi NCR | F | BCA | 84 |
| 20–25 | Delhi NCR | M | B.Sc CS | 72 |
| 20–25 | Delhi NCR | F | B.Sc CS | 95 |

The exact values have been reduced in precision while the dataset can still be used for broader statistical analysis.

---

# 7. Technique 4: Pseudonymization

Pseudonymization replaces an individual's identity with an artificial identifier.

For example:

```text
Aarav Sharma → Student_001
Riya Sharma  → Student_002
Karan Singh  → Student_003
```

The dataset can therefore contain:

| Pseudonymous ID | Age | Course | Score |
|---|---:|---|---:|
| STUDENT_001 | 21 | B.Sc CS | 86 |
| STUDENT_002 | 22 | B.Sc CS | 91 |
| STUDENT_003 | 21 | B.Sc CS | 78 |

Unlike complete anonymization, pseudonymization can potentially be reversed if an authorized mapping table exists.

Therefore, pseudonymization should not automatically be considered equivalent to complete anonymization.

---

# 8. Technique 5: k-Anonymity

**k-anonymity** attempts to ensure that every record is indistinguishable from at least **k−1 other records** with respect to selected quasi-identifiers.

For example, suppose we select:

- Age Group
- Region
- Gender

If a combination occurs four times, then those records form a group with:

```text
k = 4
```

An attacker who knows those quasi-identifiers would have at least four possible records to choose from.

### Example

| Age Group | Region | Gender | Score |
|---|---|---|---:|
| 20–25 | Delhi NCR | M | 86 |
| 20–25 | Delhi NCR | M | 78 |
| 20–25 | Delhi NCR | M | 75 |
| 20–25 | Delhi NCR | M | 72 |

These four records share the same generalized quasi-identifiers.

Therefore:

```text
k = 4
```

The individual's exact identity becomes harder to distinguish based only on these attributes.

### Important Point

Increasing the value of **k** generally provides stronger anonymity against this particular type of identification, but excessive generalization can reduce the usefulness of the dataset.

---

# 9. Technique 6: Differential Privacy

Differential privacy provides a mathematical framework for limiting how much the output of a data analysis can reveal about any single individual.

Instead of releasing individual records, an organization can release statistical results with carefully controlled random noise.

For example, suppose the actual average examination score is:

```text
Average Score = 83.4
```

A privacy-preserving system could release:

```text
Reported Average = 83.8
```

The small difference is introduced to reduce the possibility of determining whether a particular person's record was included in the dataset.

A simplified representation is:

```text
Original Dataset
       ↓
Statistical Query
       ↓
Privacy Mechanism
       ↓
Controlled Noise
       ↓
Published Result
```

Differential privacy is particularly useful when organizations need to publish statistical information without exposing individual records.

---

# 10. Practical Transformation of the Dataset

The original dataset contains:

```text
Name + Age + City + Gender + Course + Score
```

After applying privacy techniques:

```text
Name → Removed
Age → Age Group
City → Region
Gender → Retained/Generalized if required
Course → Retained
Score → Used for aggregate analysis
```

### Anonymized Dataset

| Age Group | Region | Gender | Course | Score |
|---|---|---|---|---:|
| 20–25 | Delhi NCR | M | B.Sc CS | 86 |
| 20–25 | Delhi NCR | F | B.Sc CS | 91 |
| 20–25 | Delhi NCR | M | B.Sc CS | 78 |
| 20–25 | Delhi NCR | F | BCA | 88 |
| 20–25 | Delhi NCR | M | BCA | 75 |
| 20–25 | Delhi NCR | F | BCA | 84 |
| 20–25 | Delhi NCR | M | B.Sc CS | 72 |
| 20–25 | Delhi NCR | F | B.Sc CS | 95 |

The dataset still allows analysis such as:

- Average score by course.
- Number of students in each course.
- Gender distribution.
- Score distribution.

However, direct personal identifiers are no longer included.

---

# 11. Privacy-Utility Trade-off

An important challenge in anonymization is maintaining a balance between **privacy and usefulness**.

```text
More Privacy
     ↑
     │
     │   Strong Anonymization
     │        ↓
     │   Less Detailed Data
     │
     └────────────────────→
                    More Utility
```

If too much information is removed, the dataset becomes less useful for analysis.

For example:

```text
Exact Age = 21
```

provides more information than:

```text
Age Group = 20–30
```

However, the second representation provides greater privacy.

Therefore, anonymization should be designed according to the purpose of the dataset.

---

# 12. Re-identification Risk

Anonymization does not necessarily mean that re-identification is impossible.

An attacker could combine an anonymized dataset with information obtained from another source.

For example:

```text
Anonymized Dataset
        +
Public Information
        ↓
Matching Attributes
        ↓
Possible Re-identification
```

This is known as a **linkage attack**.

Therefore, organizations should assess the risk of re-identification before releasing or sharing datasets.

---

# 13. Real-World Applications

### Healthcare

Patient information can be anonymized before being used for medical research.

### Education

Student performance data can be analyzed without publicly exposing student identities.

### Banking

Customer information can be masked before being displayed to employees.

### E-commerce

Customer behavior can be aggregated for statistical analysis without publishing individual customer identities.

### Government

Population statistics can be released while reducing the exposure of individual citizens' information.

---

# 14. Comparison of Techniques

| Technique | How It Works | Main Privacy Benefit |
|---|---|---|
| Masking | Hides part of a value | Prevents exposure of complete sensitive values |
| Suppression | Removes a field or record | Eliminates unnecessary identifiers |
| Generalization | Replaces precise values with broader categories | Reduces identification precision |
| Pseudonymization | Replaces identity with an artificial identifier | Separates identity from working data |
| k-Anonymity | Makes records indistinguishable based on selected attributes | Reduces uniqueness of individual records |
| Differential Privacy | Adds mathematically controlled randomness to outputs | Limits information about individual participation |

---

# 15. Security Recommendations

For effective privacy protection:

1. Remove unnecessary direct identifiers.
2. Generalize sensitive quasi-identifiers.
3. Use pseudonymization when controlled re-linking is required.
4. Select an appropriate value of **k** for k-anonymity.
5. Use differential privacy when publishing aggregate statistics where appropriate.
6. Assess the possibility of linkage and re-identification attacks.
7. Restrict access to original datasets.
8. Protect any mapping information used for pseudonymization.
9. Avoid collecting information that is not required.
10. Regularly review anonymization techniques as datasets and external information sources change.

---

# 16. Result

The sample student dataset was transformed using multiple privacy-preserving techniques.

Direct identifiers were removed, precise attributes were generalized, identities were replaced with pseudonymous identifiers where appropriate, and the concept of k-anonymity and differential privacy was applied to demonstrate how privacy risks can be reduced while retaining analytical value.

---

# Conclusion

Data anonymization is an important component of modern data privacy. It allows organizations to obtain useful insights from datasets while reducing the exposure of personal information.

Techniques such as **masking, suppression, generalization, pseudonymization, and k-anonymity** modify individual records, while **differential privacy** focuses on limiting what can be learned about an individual from released statistical information.

No single technique is suitable for every situation. The appropriate approach depends on the type of information, the intended use of the dataset, the required level of privacy, and the acceptable loss of analytical detail.

A successful privacy-preserving system therefore needs to balance **privacy, security, and data utility** rather than simply removing names from a dataset.

---

## References

1. NIST Privacy Framework – [NIST Privacy Framework](https://www.nist.gov/privacy-framework?utm_source=chatgpt.com)
2. NIST – De-Identification of Personal Information – [NIST De-Identification Guidelines](https://www.nist.gov/publications/de-identification-personal-information?utm_source=chatgpt.com)
3. NIST – Privacy-Enhancing Technologies – [NIST Privacy-Enhancing Technologies](https://www.nist.gov/privacy-framework/privacy-enhancing-technologies?utm_source=chatgpt.com)
4. [NIST – Differential Privacy and Data Privacy Resources](https://www.nist.gov/itl/applied-cybersecurity/privacy-engineering?utm_source=chatgpt.com)
