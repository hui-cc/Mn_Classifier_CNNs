# Machine Learning Spectroscopy
A convolutional neural network (CNN) classifier for determining the oxidation state of Manganese in electron energy-loss spectroscopy. This 1D CNN takes signals describing the bonding enviroment in transition metals and it accurately classifies the valence of the material exceeding 99% test accuracy. The CNN has proven to be robust to chemical shifts (the real-world signal is capable of sliding temporally) and is deemed temporally invariant across the energy spectrum. It is robust to noise after using PCA as a form of data augmentation. PCA is effective at modeling the real noise found in EELS signals.

## Dependencies
- HyperSpy 1.3
- Keras 1.2.1
- Tensorflow 0.12
- numpy 1.13.1
- scikit-learn 1.18
- pandas 0.18.1
- matplotlib 1.5.3

## Usage (Training)

Training a CNN
`python train.py cnn` 

Training an MLP
`python train.py MLP`

The default settings are for 1000 epochs, batch size of 512, 85/15 train-test split and no PCA data augmentation. These params are all adjustable in `train.py`.

In addition to using `train.py` there is also a Jupyter Notebook file which walks through what happens during training.
## Usage (Testing)

Test a CNN named `highest_val_acc_weights_cnn.h5` :
  
  `python test_model_accuracy.py cnn`

Compare a CNN and MLP named `highest_val_acc_weights_cnn.h5` and `highest_val_acc_weights_cnn.h5`

`python test_model_accuracy.py both`


For rapid prototyping and model development, it is advantageous sometimes to test the most recently trained set of weights in the weights folder

`python test_model_accuracy.py last`

The above line will test the most recent set of weights. To test the second last, or third last etc. set of weights, additional numbers can be specified after `last`.
`python test_model_accuracy.py last-1`, `python test_model_accuracy.py last-2`, `python test_model_accuracy.py last-3`


## Usage (Testing a trained model on an unknown EELS spectra)

The usage of using an unknown spectra is as follows:

`python test_unknown_spectra.py`

The path to the weights can be specified in the script.
The path to the EELS spectra can be specified in the script. HyperSpy is required to load the EELS file.
