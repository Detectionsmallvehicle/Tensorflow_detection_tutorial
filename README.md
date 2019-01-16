# Tensorflow_detection_tutorial
在/usr/local/models工程下新建文件夹dataset和data：

![image](https://github.com/Detectionsmallvehicle/Tensorflow_detection_tutorial/blob/master/images/1.jpg)

![image](https://github.com/Detectionsmallvehicle/Tensorflow_detection_tutorial/blob/master/images/2.jpg)

其中xml_to_csv.py和generate_tfrecord.py可在master中寻找

注意修改

def class_text_to_int(row_label):
    if row_label == 'car':
        return 1
    elif row_label == 'person':
        return 2
    elif row_label == 'truck':
        return 3
    elif row_label == 'bus':
        return 4
    elif row_label == 'other vehicle':
        return 5
    else:
        print('NONE: ' + row_label)
        # None

以及相关路径

运行完成，在data目录下产生

eval.csv, eval.record, train.csv, train.record

在data下放置labelmap.pbtxt,注意和上述文件内容保持一致

从https://github.com/tensorflow/models/tree/master/research/slim
下载模型，将 
model.ckpt.data-00000-of-00001
model.ckpt.index
model.ckpt.meta
放置在dataset文件夹下的fine_tune_model文件夹内

将下载的pipeline.config放置在dataset/data/文件夹内

修改pipeline.config中的尺寸，fine_tune_checkpoint，num_steps，label_map_path，input_path，num_examples

修改models-master/research/object_detection/model_main.py

注意在dataset下新建training文件夹，保存训练模型。

注意export PYTHONPATH，否则会报错。



