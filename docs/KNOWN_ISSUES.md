# Unresolved issues in the unchanged source

No item below was repaired. The user explicitly chose to preserve the existing files and prepare documentation only.

1. **Missing helper modules.** `utils.py`, `stn.py`, and `lpips/lpips_tf.py` are not present in the supplied source directory. Their absence blocks importing the project even before command-line help.
2. **No verified TensorFlow environment.** The inspected framework environment lacks TensorFlow/Addons/Keras. The combination of `compat.v1`, private `tensorflow.python.keras` imports, Addons transforms, and TF LPIPS needs a compatible, tested stack; a latest-version installation is not assumed sufficient.
3. **Unavailable cover path.** `TRAIN_PATH` contains the previous machine's absolute Linux directory, whereas the supplied paired data is under a different top-level `dataset/` directory. Paths are module constants, not CLI options.
4. **Unverified pairing/order.** Two unsorted `glob` lists are indexed with the same random index; matching sets of 7,080 filenames do not prove index alignment. The 7,080 bound is hardcoded rather than derived from the actual lists.
5. **Silent image fallback.** Loading errors are replaced by black arrays. A future run must verify real samples rather than using a finite loss as proof that images loaded correctly.
6. **Metric naming does not match the apparent expressions.** `get_secret_acc` rounds its input and counts nonzero predicted-minus-true differences. The returned `bit_acc` expression therefore counts mismatches, not matches. The `str_acc` expression, as written for equal-length binary arrays, selects the all-bits-different case rather than exact recovery. These summary labels must not be reported as verified bit/message accuracy. No correction or sigmoid-placement change was made here.
7. **Numerical guard absent in JND normalization.** The final JND normalization divides by `max-min` without an explicit epsilon. A zero range would cause an invalid division; this possibility was identified statically, not observed in a TensorFlow run.
8. **Staged learning assumptions.** The standalone NSN pretraining loop is commented out, and a hardcoded global-step condition switches decoding to learned-noise images after 100,000 steps. That schedule was preserved rather than interpreted as a successfully trained NSN.
9. **Side effects and long defaults.** Importing `train_f.py` may create `checkpoints/`; the default main run requests 140,000 steps. No import, `--help`, or shortened run was used as a supposedly harmless check.
10. **Output/export assumptions unverified.** The source saves into per-experiment checkpoint paths and imports a frozen graph into another session for export. Folder preparation and graph/session/tensor consistency have not been validated. No checkpoint or SavedModel was generated here.

These observations are not a full scientific audit or a declaration that every other code path is correct. They explain why this archive is documented but not claimed runnable.
