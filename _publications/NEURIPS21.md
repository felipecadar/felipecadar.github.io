---
title: "ExtractingDeformation-AwareLocal Features by Learning to Deform"
collection: publications
permalink: /publication/neurips2021
excerpt: 'In this paper, we present a new approach to compute features from still images that are robust to non-rigid deformations to circumvent the problem of matching deformable surfaces and objects'
date: 2018-11-01
venue: 'NEURIPS 2021'
paperurl: 'https://papers.nips.cc/paper/2021/hash/5934c1ec0cd31e12bd9084d106bc2e32-Abstract.html'

---

Despite the advances in extracting local features achieved by handcrafted and learning-based descriptors, they are still limited by the lack of invariance to non-rigid transformations. In this paper, we present a new approach to compute features from still images that are robust to non-rigid deformations to circumvent the problem of matching deformable surfaces and objects. Our deformation-aware local descriptor, named DEAL, leverages a polar sampling and a spatial transformer warping to provide invariance to rotation, scale, and image deformations. We train the model architecture end-to-end by applying isometric non-rigid deformations to objects in a simulated environment as guidance to provide highly discriminative local features. The experiments show that our method outperforms state-of-the-art handcrafted, learning-based image, and RGB-D descriptors in different datasets with both real and realistic synthetic deformable objects in still images. The source code and trained model of the descriptor are publicly available at https://www.verlab.dcc.ufmg.br/descriptors/neurips2021.

[Download paper here (Arxiv)](https://arxiv.org/pdf/2111.10617.pdf)

Recommended citation:
```
@INPROCEEDINGS{potje2021neurips,
author={Guilherme {Potje} and Renato {Martins} and Felipe {Cadar} and Erickson R. {Nascimento}},
booktitle={2021 Conference on Neural Information Processing Systems (NeurIPS)},
title={Extracting Deformation-Aware Local Features by Learning to Deform},
year={2021}
}
```