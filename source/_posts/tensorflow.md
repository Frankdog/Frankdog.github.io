---
title: tensorFlow
date: 2018-12-19 10:24:59
tags: tensorFlow
categories: deep learning
---

- [Tensorflow 模型](#tensorflow-模型)
  - [ckpt 模型保存](#ckpt-模型保存)
  - [ckpt 恢复](#ckpt-恢复)
  - [pb 模型保存](#pb-模型保存)
  - [pb 模型恢复](#pb-模型恢复)
  - [ckpt模型 转 pb模型](#ckpt模型-转-pb模型)
- [Tensorflow layers](#tensorflow-layers)
- [Tensorboard 使用](#tensorboard-使用)
  - [API](#api)
  - [写日志](#写日志)
  - [显示日志](#显示日志)

<!-- more -->

# Tensorflow 模型
- ckpt 模型
- pb 模型

## ckpt 模型保存
``` python
import tensorflow as tf

inputs = tf.placeholder（tf.float32,shape=[None,...],name='inputs']
...
prediction = tf.nn.softmax(logits,name='predictions')

saver = tf.train.Saver()
...

with tf.Session() as sess:
    saver.save(sess,'./xxx/xxx.ckpt')
```
## ckpt 恢复
```python
with tf.Session() as sess:
    saver = tf.train.import_meta_graph('./xxx/xxx.xxx.ckpt.meta')
    saver.restore(sess,'./xxx/xxx.ckpt')

    inputs = tf.get_default_graph.get_tensor_by_name('inputs:0')

    pred = tf.get_default_graph.get_tensor_by_name('prediction:0')

    pred = sess.run(prediction,feed_dict={inputs:xxx})
```

## pb 模型保存
```python
from tensorflow.python.framework import graph_util

···
inputs = tf.placeholder(tf.float32, shape=[None, ···], name='inputs') 
···
prediction = tf.nn.softmax(logits, name='prediction') 
···

with tf.Session() as sess:
    ...
    graph_def = tf.get_default_graph().as_graph_def()
    output_graph_def = graph_util.convert_variables_to_constants(sess,graph_def,
    ['prediction'])

    with tf.gfile.GFile('./xxx/xxx.pb','wb') as fid:
        serialized_graph = output_graph_def.SerializeToString()
        fid.write(serialized_graph)
 
```

## pb 模型恢复
```python
def load_model(path_to_model.pb):
    if not os.path.exists(path_to_model.pb):
        raise ValueError("'path_to_model.pb' is not exist.")

    model_graph = tf.Graph()
    with model_graph.as_default():
        od_graph_def = tf.GraphDef()
        with tf.gfile.GFile(path_to_model.pb, 'rb') as fid:
            serialized_graph = fid.read()
            od_graph_def.ParseFromString(serialized_graph)
            tf.import_graph_def(od_graph_def, name='')
    return model_graph

model_graph = load_model('./xxx/xxx.pb')

inputs = model_graph.get_tensor_by_name('inputs:0')
prediction = model_graph.get_tensor_by_name('prediction:0')

with model_graph.as_default():
    with tf.Session(graph=model_graph) as sess:
        ···
        pred = sess.run(prediction, feed_dict={inputs: xxx} 
```

## ckpt模型 转 pb模型
```python
from tensorflow.python.framework import graph_util

with tf.Session() as sess:
    # Load .ckpt file
    saver = tf.train.import_meta_graph('./xxx/xxx.ckpt.meta')
    saver.restore(sess, './xxx/xxx.ckpt')

    # Save as .pb file
    graph_def = tf.get_default_graph().as_graph_def()
    output_graph_def = graph_util.convert_variables_to_constants(
        sess, 
        graph_def, 
        ['prediction']  <-- 输出节点名，以实际情况为准
    )
    with tf.gfile.GFile('./xxx/xxx.pb', 'wb') as fid:
        serialized_graph = output_graph_def.SerializeToString()
        fid.write(serialized_graph) 
```


# Tensorflow layers
- tf.layers.Input
- tf.layers.conv2d
- tf.layers.max_pooling2d
- tf.layers.dense
- tf.layers.dropout



# Tensorboard 使用
## API
```
tf.summary.scalar
tf.summary.histogram
tf.summary.distribution
tf.summary.text
tf.summary.image
tf.summary.audio
tf.summary.merge_all
tf.summary.FileWriter
```
## 写日志
```python
import tensorflow as tf

with tf.Session() as sess:
    ...
    tf.summary.merge_all()
    tf.summary.FileWriter('logs/',sess.graph)
```
## 显示日志
```
tensorboard --logdir=logs
```
