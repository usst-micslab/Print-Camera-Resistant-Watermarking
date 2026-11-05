# Preparation and validation record

Date: **2026-11-05**. The user explicitly requested **existing files and documentation only**, without dependency installation or repair.

| Check | Result |
| --- | --- |
| Supplied source inventory | Two Python files: `model_f.py` and `train_f.py` |
| Static syntax compilation / AST parsing | Both passed, without executing imports |
| Source preservation | Copied byte-for-byte; SHA256 values recorded in `source_sha256.txt` |
| Missing-module review | Local `utils`, `stn`, and TensorFlow LPIPS implementation absent |
| Paired data inventory | 7,080 JPG filenames in each noise-data folder; matching name sets |
| Data content/alignment | Not verified; complete datasets not copied |
| Available framework-environment query | Read-only package metadata check; no TensorFlow/Addons/Keras present in the inspected environment |
| Dependency installation / new execution environment | Not performed |
| Model import / graph construction | Not performed |
| Training step / inference / watermark recovery | Not performed |
| Checkpoint restoration / pretrained results | Not performed; no project checkpoint supplied |
| Physical print-camera robustness | Not performed |
| Paper metadata | Supplied accepted-author PDF and Crossref DOI record checked |

No successful-runtime, bit-accuracy, visual-quality, or paper-reproduction claim is made. The core source was not modified and no helpers were borrowed or fabricated. All scientific/runtime limitations in the original code remain present.

The paper header was rendered from the supplied PDF and visually inspected; the full paper and preparation caches are kept outside the public project file set. Datasets, weights, logs, environments, and the original large archive are excluded from release.

Selected-file checksums and relative Markdown/image links are checked before delivery, and upload exclusions are tested using a disposable Git index. The actual project directory is not initialized/committed/pushed during documentation-only preparation.

Final package audit: the original and copied SHA256 values both matched for both Python files; both files compiled statically. All nine relative Markdown/image links resolved. A disposable Git index contained 12 public files, and all 12 ignored-path test cases stayed out of the index. The release-file audit returned no candidates requiring review. This verifies the package boundaries, not runtime behavior.
