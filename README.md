# Behavox Email Challenge

## Training Model
To run the model run the command:

```bash
python run.py
```


## Trained Model

What I found to be the best model is a bidirectional LSTM in conjunction with a sigmoid classifier layer. The input is a series of word embeddings (from a pre-trained FastText word embedding) representing the email. Stop words like "the" are removed as they do not give a great benefit to the inpretation of the email by the model. 

Lines specifying the email addresses it is going to and from are removed as well to help generalize the model. Certain emails could have a much higher correlation with the personal class which should give little to no real information to what class the email is. Removing this information would help reduce the noise of the data and improve the generalizablity of the model. 

I used a variety of configurations to get the model below, but they can still be optimized further. Interesting, increasing the number of parameters for the LSTM worsen the model.

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
input_1 (InputLayer)         (None, 512, 300)          0
_________________________________________________________________
bidirectional_1 (Bidirection (None, 50)                65200
_________________________________________________________________
dense_1 (Dense)              (None, 1)                 51
=================================================================
Total params: 65,251
Trainable params: 65,251
Non-trainable params: 0
_________________________________________________________________
```

__test loss__: 0.16246534883975983

__test accuracy__: 0.958984375