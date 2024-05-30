## Cat - Dog Classifier

**Clone Repo**
```
git clone https://github.com/shoryasethia/Cats-Dog-InceptionV3
cd Cats-Dog-InceptionV3
```

**Dataset**
- Download it from [here](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
  
# **Transfer Learning**
- Used **`InceptionV3`** as base model
```
from tensorflow.keras.applications.inception_v3 import InceptionV3

pre_trained_model = InceptionV3(input_shape = (150, 150, 3),
                                include_top = False,              
                                weights = None)           
```
- Used weights of **`Imagnet`** dataset, downloaded from [here](https://github.com/fchollet/deep-learning-models/releases/download/v0.7/inception_resnet_v2_weights_tf_dim_ordering_tf_kernels_notop.h5:)
```
pre_trained_weights_file = 'inception_v3_weights_tf_dim_ordering_tf_kernels_notop.h5'

pre_trained_model.load_weights(pre_trained_weights_file)
```
- Freezed those weights and removed/discarded last few layers
```
pre_trained_model.trainable = False   
```
- Added following layers further
```
Model: "sequential_1"
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓
┃ Layer (type)                    ┃ Output Shape           ┃       Param # ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩
│ functional_2 (Functional)       │ ?                      │    18,191,008 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ flatten_1 (Flatten)             │ ?                      │   0 (unbuilt) │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_3 (Dense)                 │ ?                      │   0 (unbuilt) │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_4 (Dense)                 │ ?                      │   0 (unbuilt) │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_5 (Dense)                 │ ?                      │   0 (unbuilt) │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_6 (Dense)                 │ ?                      │   0 (unbuilt) │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_7 (Dense)                 │ ?                      │   0 (unbuilt) │
└─────────────────────────────────┴────────────────────────┴───────────────┘
 Total params: 18,191,008 (69.39 MB)
 Trainable params: 0 (0.00 B)
 Non-trainable params: 18,191,008 (69.39 MB)
```
**Got Accuracy of `0.9575660824775696` on Test Dataset**
![Predictions](https://github.com/shoryasethia/Cats-Dog-InceptionV3/blob/main/some-predictions.png)

**Download My Fine Tuned InceptionV3 Model**
- **[FineTuneInception.h5](https://drive.google.com/file/d/1aAjA-2k70iQQ19h_n7uC1GhgOUNVH0RC/view?usp=sharing)**
- **[FineTuneInception.weight.h5](https://drive.google.com/file/d/1XCSUoCX6wIY1ObxXFzEDVQMTXMPlUeuX/view?usp=sharing)**

- If this repo helped in nay way, give it a like
- Author : [@shoryasethia](https://github.com/shoryasethia)
