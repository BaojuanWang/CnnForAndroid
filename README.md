## CnnForAndroid:A Classification Project using Convolutional Neural Network(CNN) in Android platform。It also support Caffe Model

CnnForAndroid is a android platform's implementation of deep learning using Tiny-cnn structure and provide two Recognition sample:one is gender Recognition for caffe net ; two is Car logo recognition for tiny-cnn net.

# Todo List

* add opencl support.
* change to the tiny-dnn new version
* Optimise the code and improve the speed.

# Dependencies

[Opencv](http://opencv.org/)(for Android platform Opencv-2.4.9)

[Tiny-cnn](https://github.com/nyanp/tiny-cnn#features)(old Version)

[protobuf](https://github.com/google/protobuf)

# Supporting Caffe model

tiny-cnn provide the caffe-convertor.cpp to support the caffe model.The project also support the caffe model from  compiling the caffe_convertor and protobuf.

# For Gender Recogniton

 this project also provide a sample for caffe model to distingguish man from woman also called gender recognition. 
 	
 1.Where from training data?
 	
 	MORPH Album 2.
 	
 	the test accuracy is 90.01% in my caffe's net.
 	
 2.the net of caffe ?
	
![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/net.PNG)
	
 3.How to train yourself caffe's model?
 	
 	(1)Please using caffe and train your model.     
 	(2)then replace  /assets/tinyfile//.caffemodel and /assets/tinyfile/*.protobuf file/.
 	(3)Finish  change those filenames in tinyCnn.java file.

# How to install it?
 	
 	no need install.

	Just download or git clone it and then open it by eclipse with opencv for java lib ,  use NDK to build it.
 	Surely your libs docu have the opencv_java.so file or you must add this file(from Opencv-android docu).
 	
[APK Download](https://raw.githubusercontent.com/zhangqianhui/CnnForAndroid/master/bin/tiny-cnn.apk)
 
# Compile it 
 
 needful tools： NDK + eclipse + adt.
 
 or android studio.
 
#For Vehicle Recogniton for tiny-cnn net 

1.What is Vehicle Recognition?

 this project classify car according to car logo.Now  the lasting Version just distinguish VM car from other.

2.Where from Training Data ?

The major sources of our dataset include images captured by ourselves,Medialab LPR Dataset [1].

![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/20.jpg)
![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/21.jpg) 

3.this models?

You can get it in JNi/test.cpp file.

Code:
```cpp

  static const bool tbl[] = {
			O, X, O, O, O, O, O, O, O, O, O, X, O, O, O, O,
			O, X, X, X, O, O, O, X, X, O, O, O, X, X, O, O,
			O, O, X, X, X, O, O, O, X, X, O, O, X, X, X, O,
			O, O, O, X, X, X, O, O, O, X, X, O, X, X, O, O,
			O, O, O, O, X, X, O, O, O, O, X, X, O, X, X, O,
			O, X, O, O, O, X, X, O, O, O, O, X, O, O, X, O,
	};

	 nn << convolutional_layer<tan_h>(40 , 40 , 3 , 1 , 6)  
		<< average_pooling_layer<tan_h>(38 , 38 , 6 , 2)   
		<< convolutional_layer<tan_h>(19 , 19 , 4 , 6 , 16 ,
		connection_table(tbl, 6, 16))              
		<< average_pooling_layer<tan_h>(16 , 16 , 16 , 2)  
		<< convolutional_layer<tan_h>(8 , 8 , 3 , 16, 16) 
		<< fully_connected_layer<tan_h>(16 * 6 * 6 , 64)
		<< fully_connected_layer<relu>(64 , 2);
		
```
 My models have three conv-layers and two pooling layer , fully-connect layer , in the end layer , the activation functions is relu and the size of all conv-kernel is 3x3.The optimization algorithm of cnn  is stochastic gradient levenberg marquardt.
 
 Other arguments can't be public.
 
 4.Experiment 
 
 	data：
 
		 500 train image , 298 test image.
 
 	platform:
 
 		Windows+VS2013.
 	Result:
 		 the recognition rate is above 94.29% 
 		 
 ![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/test.PNG)
 
 		
 
# How to use it to recognize face or other object?

If want to recognition other object , you must learning Cnn and tiny-cnn , contructing optimal model and training it using 
enough object images to get the wb-file(weights and bias values).Finish , replace /assets/tinyfile/carlogo file with wb-file.

# References 

[1]Medialab LPR dataset, March. 2013[online]. Available: http://www.medialab.ntua.gr/research/LPRdataset.html

[2]Humayun Karim Sulehria, Ye Zhang.Vehicle Logo Recognition Using Mathematical Morphology

[3]Humayun Karim Sulehria, Ye Zhang.Vehicle Logo Recognition Based on Bag-of-Words.IEEE International Conference on Advanced Video and Signal Based Surveillance,2013.

# Running Screenshot

(1)For Vehicle Recogniton

![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/23.png)
![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/24.png) 

(3)For gender Recognition

![](https://github.com/zhangqianhui/CnnForAndroid/blob/master/photo%20for%20readme/app.png)

# Discussing
* [issue](https://github.com/zhangqianhui/CnnForAndroid/issues/new)
* email:zhang163220@gmail.com
