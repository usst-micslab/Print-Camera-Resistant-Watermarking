# External data, resource paths, and intended outputs

## Supplied paired image inventory

The original resource tree contains:

```text
dataset/
  train_class/       # 7,080 JPG filenames
  train_ps_class/    # 7,080 JPG filenames
```

The two filename sets match. The images were not exhaustively opened, checked for alignment, modified, or copied into this release. No data-quality or physical-capture validation is inferred from matching names.

The training entry instead looks for `./train_class` and `./train_ps_class` relative to its process working directory. With `train_code/` as the intended working directory, it expects:

```text
train_code/
  train_f.py
  model_f.py
  train_class/       # External resource, excluded from Git
  train_ps_class/    # External resource, excluded from Git
```

Alternatively, the module-level constants could be updated to authorized external directories during a future restoration. This preparation did not change them or create links/copies of those datasets.

## Cover-image training data

`TRAIN_PATH` is an absolute Linux path belonging to the previous machine. It is not available simply because the paired folders exist. The code samples random cover images from a separate file list and generates random binary messages; neither the hardcoded path nor a `--train_path` CLI option was added or fixed.

Unreadable cover/paired images are silently replaced with zeros in the loaders. That fallback should not be interpreted as successful data loading.

## Pairing caveat

The two noise-data lists are collected with separate `glob` calls and are not explicitly sorted or joined by filename. The same random index is applied to both lists, with a hardcoded upper bound of 7,080. Matching filename sets alone do not guarantee that the same index selects a matching pair. These assumptions need explicit verification before a future run.

## Checkpoints and exports

No pretrained checkpoint or exported SavedModel is included in the supplied project tree. The source defines `--pretrained` for a TensorFlow checkpoint **prefix**, for example the prefix shared by `.index` and `.data-...` files; it is not a PyTorch `.pth` file.

The source is intended to write `./logs/<exp_name>/`, periodically save under `./checkpoints/<exp_name>/`, and finally export under `./saved_models/<exp_name>/`. A `checkpoints/` root can be created at module import time. Per-experiment directory creation and the final graph/session export assumptions need review before execution.

The encoder/deployment tensors expect 400 x 400 images, and the default message length is 100 bits. These are static code observations, not evidence of a trained or validated system.
