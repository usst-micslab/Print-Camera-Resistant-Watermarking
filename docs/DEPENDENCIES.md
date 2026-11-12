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

## Candidate helper sources

The public upstream tree omits all three helpers. The following references were checked against the call sites without importing the project.

| Import expected by this project | Reference and evidence | Verification needed |
| --- | --- | --- |
| `utils.py` | [StegaStamp utils.py](https://github.com/tancik/StegaStamp/blob/c984446048b826587ca1875027b0a1dc1885fb30/utils.py) defines all five required functions with matching signatures. An [upstream issue participant](https://github.com/davidgdd1/Print-Camera-resilient-watermarking/issues/2#issuecomment-2434473935) reports resolving the missing `utils` import using that source. | Check legacy TensorFlow calls in the intended graph-mode environment. |
| `lpips/lpips_tf.py` | [LPIPS TensorFlow port](https://github.com/alexlee-gk/lpips-tensorflow/blob/87bea09959fe030e6fd4af31bc499dfb7e998f93/lpips_tf.py) exposes the two-image `lpips(...)` call. This revision is the LPIPS submodule pinned by StegaStamp. | Check graph-mode compatibility, input ranges, and availability of the separate perceptual model asset. |
| `stn.py` | [Kevin Zakka's TensorFlow STN](https://github.com/kevinzakka/spatial-transformer-network/blob/375f99046383316b18edfb5c575dc390c4ee3193/stn/transformer.py) accepts an image batch, six affine parameters per image, and output dimensions, matching the shape of the decoder call. | The authors' exact `stn.py` remains unidentified. Verify the coordinate convention, interpolation, and gradients before adopting a replacement. |

The references establish static compatibility clues. Runtime behavior remains unverified. The archive contains no substitute helper implementations or verified environment lock.
