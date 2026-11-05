# External Image Test Log

These manual spot checks are separate from the PlantDoc 134-image benchmark.

| Case | Reference | Top prediction | Score | Outcome |
|---|---|---|---:|---|
| 1 | Possibly grape erineum mite; exact label unconfirmed | Apple Cedar Rust | 39.55% | Not a valid scored test; likely unsupported condition |
| 2 | Grape Black Rot | Apple Cedar Rust | 65.50% | Incorrect top prediction; expected class not in top three |

See [failure analysis](../../docs/failure-analysis.md) for the full top-three outputs and interpretation.

Do not calculate accuracy from this small, selectively chosen set. Add future cases only when the source image, reference label, source URL, model checkpoint and complete prediction output are recorded.
