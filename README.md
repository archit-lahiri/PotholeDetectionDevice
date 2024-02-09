# PotholeDetectionDevice

video demo (proof of concept): [here](https://drive.google.com/file/d/1Hpt28FcrFKwXlsGwkzL7xro4kgT3ilEZ/view?usp=sharing)

An attachable accessory device for industrial vehicles that detects potholes on the road and alerts the driver using an alerting component such as an LED or a buzzer. The device consists of an attachable container within which there is a camera and a Raspberry Pi that is connected. The camera acts as a sensor to provide images to the model to evaluate if there is a pothole or not in front of the device. The camera has a field of view of 32.4 feet. The camera will be positioned under and in front of the vehicles, and the alerting component will be present near the driver and connected through the container to the GPIO pins of the Raspberry Pi. In future tests, we will use global shutter cameras to improve the field of view and image quality.

A specialized fine-tuned machine learning architecture is installed into the Raspberry Pi that performs the classification of potholes and good roads. The model has been verified and validated based on the accuracy measurements that were above 90% in test sets, and qualitatively in the proof of concept as the device detected images of potholes. 

Iandola (2016) describes the squeezenet architecture that requires less than 0.5 MB of space and is capable of performing ML tasks with similar accuracy to that of AlexNet, a much bigger model. This was specifically designed for devices like mobile phones and the Raspberry Pi. 

Yolo models used in the patents in the past patent section are much larger in comparison and cannot be run on the Raspberry Pi as stated by Ameen (2023). While smaller variants exist, like the “tiny” variant of Yolo, it is less accurate than other larger counterparts. Also without the need to produce bounding boxes, Yolo models are not necessary for this application, and Squeezenet is sufficient. 

Due to their smaller size in memory, Squeezenet models are ideal for a Raspberry Pi. From Velasco-Montero et al.(2018), we can conclude that Squeezenet models function well in a Raspberry Pi which can also be seen in Sahoo et al.(2022) as it shows a practical use case. Whereas from Ameen et al. we can conclude that the larger versions of YOLO will not perform well. From this, we can see that using the Squeezenet model is the better option in terms of performance on the Raspberry Pi while maintaining high levels of accuracy.

Beyond this, prototyping and real-time testing need to be done.

 As the vehicle drives, the camera inputs an image stream into the Raspberry Pi, which the machine learning model uses to detect potholes, and if found, within seconds, signals are sent to the alerting component to alert the driver for their safety and to avoid unnecessary damages to the vehicle.  

This invention informs the driver of upcoming potholes within the camera’s field of view and the driver can react accordingly. This can save lots of money in potential damages for industrial vehicles (like trucks) and prevent accidents. Our invention can perform pothole detection locally as it uses state-of-the-art lightweight models that can be run on a Raspberry Pi and fine-tuned for this particular task to increase its accuracy.
