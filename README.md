# GlaucomaDetection
Development and analysis of various deep NN models to detect glaucoma cases from fundus images. The performance of the best model was evaluated with cross-validation. Mean F1-score: 0.95975, with a standard deviation of 0.02274.

- The first 3 configuartions are built over an EfficientNet B0 feature extractor, pretrained with ImageNet weigths, adding a classification head composed by a GlobalAveragePooling2D layer, a BatchNormalization layer, a Dropout layer (0.2) and at the end a fully connected layer.  
  - The 1st model is built training just the classification head, freezing all others layers.  
  - The 2nd model is trained starting from the weights of the first model, unfreezing the last 20 layers (BatchNorm layers excluded).  
  - The 3rd model is trained starting from the weights of the second model, unfreezing all the layers (BatchNorm layers exluded).

- The 4th model is built on a ResNet50 feature extractor, pretrained on the ImageNet dataset. On top of the feature extractor, that is set as untrainable during the training, is built a classification head that consists of 4 layers, analogously to what was done in model 1: GlobalAveragePolling2D, BatchNormalization, dropout (0.2), and at the end a FC layer.

- The 5th is built on a Xception feature extractor, pretrained on the ImageNet dataset. On top of the feature extractor was built a classification head that consists of 4 layers, analogously to what was done in model 1 and 4.
