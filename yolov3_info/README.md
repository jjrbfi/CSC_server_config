# Yolov3 configurations and commands:

## 🗜 Yolov3 config:
See the file: [Yolov3-nai20sp.cfg](https://github.com/jjrbfi/CSC_server_config/blob/main/yolov3_info/yolov3-nai20sp.cfg)

## 🛠 Doing a training:
```
./darknet detector train data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg ../darknet53.conv.74
```
If we don't want to have the chart appear into the screen when training is running. Add this flag at end of command: **-dont_show**

The same flag it's used to get plot or our key metrics in the terminal.

## 📝 Saving output to a text file:
If you want/need to have all the output in one text file named **log** you have to add this at the end of the command:
```
2>&1 > log.txt
```


## 📈 Calculating (mAP), precision, recall and other metrics.
In order to get the metrics. Add the flag **-map** at the command:
```
./darknet detector train data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg ../darknet53.conv.74 -map -dont_show
``` 

## 📊 Evaluating model on validation data:
```
./darknet detector map data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg data/my_test_data/backup/yolov3-nai20sp_best.weights
```

## 🏷 Test a group of images and save the result in a text file (result.txt):
The group of files in this example are localed at (data/my_test_data/test.txt)
```
./darknet detector test data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg data/my_test_data/backup/yolov3-nai20sp_final.weights -dont_show -ext_output < data/my_test_data/test.txt > result.txt
```

## 🎥 Creating prediction from input_video.mp4 and save it into output_video.mp4:
```
./darknet detector demo data/my_test_data/obj.data cfg/yolov3-nai20sp.cfg data/my_test_data/backup/yolov3-nai20sp_last.weights input_video.mp4 -i 0 -out_filename output_video.avi -dont_show
```
---

# Other interesting commands:

## 📑 Check how many lines we have in a file:
In this example we used the **test.txt** file, you can change that for **train.txt** or whatever to see how many images we have.
```
wc -l /opt/work/darknet/data/my_test_data/test.txt | awk '{print $1}'
```
## 🖼 Count images in current directory:
```
find . -type f -print0 | xargs -0 file -i | grep -i image | wc -l
```

## Convert all images from jpge to jpg:
```
ls | grep -v jpg$ | while IFS= read -r FILENAME; do     convert "${FILENAME}" "${FILENAME%.*}.jpg"; done
```


# 📃 Scripts

#### [Image augmentation with imgaug](https://github.com/dnissimi/imgaug-yolov3)
#### [Scripts to work with the images and label files](https://github.com/oskarforssell/ai_project)
