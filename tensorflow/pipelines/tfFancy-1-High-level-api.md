# Fancy Tensorflow

[TOC]

- Based on [tensorflow official guide](https://www.tensorflow.org/guide)

## 1.1 Keras

### Code

```python
#%% 1. Load
import tensorflow as tf
from tensorflow.keras import layers
import numpy as np

data = np.random.random((1000, 32))
labels = np.random.random((1000, 10))

print(tf.VERSION)
print(tf.keras.__version__)

#%% 2. Build Model
model = tf.keras.Sequential([
    # Adds a densely-connected layer with 64 units to the model:
    layers.Dense(64, activation='relu'),
    # Add another:
    layers.Dense(64, activation='relu'),
    # Add a softmax layer with 10 output units:
    layers.Dense(10, activation='softmax')])

#%% 3. Training and Evalutation
model.compile(optimizer=tf.train.AdamOptimizer(0.001),
              loss='categorical_crossentropy',
              metrics=['accuracy'])

model.fit(data, labels, epochs=10, batch_size=32)
```

### Notes
