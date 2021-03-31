# Yolov3 configurations and commands:

## Yolov3 config:
See the file: [Yolov3-nai20sp.cfg](https://github.com/jjrbfi/CSC_server_config/blob/main/yolov3_info/yolov3-nai20sp.cfg)

## 🛠 Doing a training:
```
./darknet detector train data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg ../darknet53.conv.74
```
If we don't want to have to get the chart appear into the windows when training is running, add this flag at end of command:
**-dont_show**

The same flag it's used to get plot or our key metrics in the terminal.

## 📝 Saving output to a text file:
If you want/need to have all the output in one text file named **log** you have to add this at the end of the command:
```
2>&1 > log.txt
```


## 📈 Calculating (mAP), precision, recall and other metrics.
```
./darknet detector train data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg ../darknet53.conv.74 -map -dont_show
``` 
In order to get mAP, precision, recall and other metris. Add this flag at end of the command:
**-map**

## 📊 Evaluating model on validation data:
```
./darknet detector map data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg data/my_test_data/backup/yolov3-nai20sp_best.weights
```

## 🎥 Creating prediction from input_video.mp4 and save it into output_video.mp4:
```
./darknet detector demo data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg data/my_test_data/backup/yolov3-nai20sp_last.weights input_video.mp4 -i 0 -out_filename output_video.avi -dont_show
```
