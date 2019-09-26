### MLP:
   #### Parameters:
   - Depth: 3 hidden Dense layers
   - Batch Size: `512`
   - Optimizer: `rmsprop`
   - Loss Function: `categorical_crossentropy`
   - Epochs: `41`

| Layer Type   | Parameters         |
| ------------ | ------------------ |
| Dense        | 1024 units, ReLU activation |
| Dropout      | 0.3 dropout rate   |
| Dense        | 1024 units, ReLU activation |
| Dropout      | 0.3 dropout rate   |
| Dense        | 1024 units, ReLU activation |
| Dropout      | 0.3 dropout rate   |
| Dense        | 10 units, Softmax activation |

   #### Results:
   After `41` epochs of training using the entire training set (50000 images), the network was able to achieve
   a loss of `1.488067834663391` and an accuracy of `0.491` when evaluated on the entire test set (10000 images).

### CNN:
   #### Parameters:
   3 convolutional layers, with varying numbers of filters and each with a 4 by 4 kernel. The optimizer used was RMSprop, with a batch size of `32` and `categorical_crossentropy` as the loss function.
   - Depth: 3 convolutional layers
      - Filters: `32`, `64`, `128`
      - Kernel Size: `4x4`
      - Padding: `same`
      - Activation: `relu`
   - Batch Size: `32`
   - Optimizer: `rmsprop`
   - Loss Function: `categorical_crossentropy`
   - Epochs: `10`

| Layer Type   | Parameters         |
| ------------ | ------------------ |
| Conv2D       | 32 filters, 4x4 kernel <br> ReLU activation, same padding |
| MaxPooling2D | 2x2 pool size      |
| Conv2D       | 64 filters, 4x4 kernel <br> ReLU activation, same padding |
| MaxPooling2D | 2x2 pool size      |
| Conv2D       | 128 filters, 4x4 kernel <br> ReLU activation, same padding |
| MaxPooling2D | 2x2 pool size      |
| Flatten      |                    |
| Dropout      | 0.35 dropout rate  |
| Dense        | 10 units, Softmax activation |

   #### Results:
   After 10 epochs of training using the entire training set (50000 images), the network was able to achieve
   a loss of `0.8567563549995423` and an accuracy of `0.7284` when evaluated on the entire test set (10000 images).

## Comparison:
   From the results of the two networks, it is clear that the CNN is superior to the MLP by a large margin (at least on this kind of classification task). The MLP network wasn't able to get above 50% accuracy, while the CNN was easily able to pass that even without much fine-tuning. __The CNN is around 1.5 times more accurate than the MLP network, and has 1.7 times less loss__.
   
   One thing to note here is that CNN takes much longer to train than the MLP. On average, each epoch of the MLP took 2s, while for CNN this value is 17s (this disparity may be attributed in part to the difference in their batch sizes). Because of this, MLP took less than half the training time of CNN even though it has 4 times the number of epochs.
