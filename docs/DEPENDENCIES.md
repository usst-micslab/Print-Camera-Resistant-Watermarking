# Dependency inventory — no installation performed

The user chose documentation-only preparation on 2026-11-05. No new environment was created, and no TensorFlow/package/helper installation or substitution was performed. An existing environment was inspected read-only; it is not presented as a valid execution environment for this project.

## Imports visible in the two supplied files

| Import / feature | Requirement and status |
| --- | --- |
| `numpy` | Numeric arrays and random message generation; no original version lock supplied |
| `PIL.Image`, `PIL.ImageOps` | Pillow image loading/fitting; no project-tested version established |
| `tensorflow.compat.v1` | Graph/session APIs, placeholders, optimizers, deployment export |
| `tensorflow.python.keras.*` | Private model/layer imports; compatibility must be verified rather than assumed |
| `tensorflow_addons.image.transform` | External image-transform API used by the training graph |
| `utils` | Missing local module; functions listed below |
| `stn.spatial_transformer_network` | Missing local spatial-transformer implementation |
| `lpips.lpips_tf.lpips` | Missing TensorFlow perceptual-loss implementation and any required model assets |

The required `utils` symbols are `get_rand_transform_matrix`, `get_rnd_brightness_tf`, `random_blur_kernel`, `jpeg_compress_decompress`, and `round_only_at_0`. Installing an unrelated package named `utils` is not a verified solution.

The inspected Python 3.10.20 framework environment had no installed TensorFlow, tensorflow-intel, TensorFlow Addons, or Keras distribution. That check does not exhaust every possible environment on the computer. No environment is claimed runnable here, and no guessed version pins or automatic upgrade instructions are supplied.

Future restoration should use a project-specific environment, verify matching TensorFlow/Keras/Addons/helper versions, and inspect helper/model licensing and required pretrained perceptual resources. Those actions require a separate repair request; the current archive intentionally stops before them.
