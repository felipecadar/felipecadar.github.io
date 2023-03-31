---
title: "Learning Geodesic-Aware Local Features from RGB-D Images"
collection: publications
permalink: /publication/sibgrapi2023
excerpt: 'In this work, we address the problem of creating smooth fast-forward videos without losing the relevant content'
date: 2023-01-01
venue: 'SIBGRAPI 2022'
paperurl: 'https://sol.sbc.org.br/index.php/sibgrapi/article/view/22896'

---
Most of the existing handcrafted and learning-based local descriptors are still at best approximately invariant to affine image transformations, often disregarding deformable surfaces. In this paper, we take one step further by proposing a new approach to compute descriptors from RGB-D images (where RGB refers to the pixel color brightness and D stands for depth information) that are invariant to isometric non-rigid deformations, as well as to scale changes and rotation. Our proposed description strategies are grounded on the key idea of learning feature representations on undistorted local image patches using surface geodesics. We design two complementary local descriptors strategies to compute geodesic-aware features efficiently: one efficient binary descriptor based on handcrafted binary tests (named GeoBit), and one learning-based descriptor (GeoPatch) with convolutional neural networks (CNNs) to compute features. In different experiments using real and publicly available RGB-D data benchmarks, they consistently outperforms state-of-the-art handcrafted and learning-based image and RGB-D descriptors in matching scores, as well as in object retrieval and non-rigid surface tracking experiments, with comparable processing times. We also provide to the community a new dataset with accurate matching annotations of RGB-D images of different objects (shirts, cloths, paintings, bags), subjected to strong non-rigid deformations, for evaluation benchmark of deformable surface correspondence algorithms.

[Download paper here](http://sibgrapi.sid.inpe.br/col/sid.inpe.br/sibgrapi/2022/09.20.19.24/doc/melo-44.pdf)
[ArXiv](https://arxiv.org/abs/2212.09589)
[Source Code](https://github.com/verlab/LearningToDetect_SIBGRAPI_2022)
[(Soon) Complete Paper Page](verlab.dcc.ufmg.br/descriptors/)

Recommended citation:
```
@inproceedings{melo22,
 author = {Welerson Melo and Guilherme Potje and Felipe Cadar and Renato Martins and Erickson Nascimento},
 title = {Learning to Detect Good Keypoints to Match Non-Rigid Objects in RGB Images},
 booktitle = {Anais do XXXV Conference on Graphics, Patterns and Images},
 location = {Natal/RN},
 year = {2022},
 keywords = {},
 publisher = {SBC},
 address = {Porto Alegre, RS, Brasil},
 url = {https://sol.sbc.org.br/index.php/sibgrapi/article/view/22896}
}
```