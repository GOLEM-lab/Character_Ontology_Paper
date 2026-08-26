# Error Analysis of Sentence-BERT Feature Matching

## Scope

This report evaluates the Sentence-BERT-based matching of raw character-feature
values to the GOLEM controlled vocabulary. Two datasets are considered:
(1) feature values occurring in the case-study RDF data, exported at cosine
thresholds of 0.70, 0.80, and 0.85; and (2) a manually annotated set of 238 raw
values used in the controlled-vocabulary coverage evaluation.

Sentence-BERT is treated as a candidate-ranking mechanism rather than the final
authority. The operational rule accepts a top-ranked mapping automatically at
scores of at least 0.85, sends scores from 0.70 to below 0.85 to manual review,
and rejects scores below 0.70.

## Case-study results

| Threshold | Unique top-1 mappings | Correct | False positives | Precision |
|---:|---:|---:|---:|---:|
| 0.70 | 28 | 23 | 5 | 82.1% |
| 0.80 | 14 | 12 | 2 | 85.7% |
| 0.85 | 10 | 10 | 0 | 100.0% |

At 0.85, the 10 accepted unique mappings correspond to 39 feature occurrences
in the RDF data. The five top-1 errors at 0.70 were `wet hair → Hair`,
`king of gods → mythological king`, `king of the gods → mythological king`,
`queen of Sparta → Sparta`, and `sapling → sapper`. These represent
part/category confusion, related-but-not-equivalent concepts, cross-category
confusion, and lexical similarity without semantic equivalence.

## Coverage-set results

Under the supported-component criterion, 166 of the 238 raw values were
considered matchable.

| Threshold | TP | FP | FN | Precision | Recall | F1 |
|---:|---:|---:|---:|---:|---:|---:|
| 0.70 | 147 | 19 | 19 | 88.6% | 88.6% | 88.6% |
| 0.80 | 124 | 1 | 42 | 99.2% | 74.7% | 85.2% |
| 0.85 | 105 | 0 | 61 | 100.0% | 63.3% | 77.5% |

Lowering the threshold from 0.85 to 0.80 accepts 20 additional values:
19 true positives and one false positive. The recovered values include
`Japanese → Japan`, `Jedi Master → Jedi`, `blue → Blue (Eyes)`, and
`strawberry blond hair → Blond (Hair)`. Forty-two matchable values remain
false negatives at 0.80, predominantly occupations (35 cases), followed by
nationalities (5), eye descriptions (1), and hair descriptions (1).

Most false positives at 0.70 arise from long, compound, or work-specific ability
descriptions for which no single clean vocabulary concept exists. Under a
stricter label-level criterion, partial and narrower mappings are counted as
errors; precision at 0.85 then decreases from 100.0% to 95.2%. This sensitivity
shows that the reported result depends on whether supported components and
hypernyms are considered acceptable mappings.

## Decision and limitations

The 0.85 threshold is retained as a precision-oriented automatic-acceptance
rule. Lower-scoring mappings require human review because embedding similarity
may conflate related concepts, character roles and locations, parts and
properties, or lexically similar but unrelated terms.

The case-study sample is small, and its exported files do not retain source
feature categories. Field-scoped matching therefore cannot be verified from
these exports alone. In addition, the 0.80 coverage metrics include an
annotation-based reconstruction of 20 values whose top-1 labels were not
persisted in the earlier output. Future releases should export the top-ranked
label, URI, score, source field, gold concept, and decision for every raw value
at every threshold. A fully automated workflow would also require evaluation
of a domain-adapted embedding model on a larger and more diverse benchmark.
