# Forecasting-Business-KPI

## Aim

To find the KPI metrics for each brand logo, such as the number of appearances of the logo,
the area, frames, shortest and longest area percentage, for the given input video clip.

## Tech stack
- Language - Python
- Libraries – TensorFlow, pillow, opencv, matplotlib, NumPy, uuid

## Approach

1. Download the input video
  - From YouTube
  - Using python (Youtube_downloader.py)

2. Use the annotation tool (LabelImg) to convert the images into XML file

3. Set up tensorflow for object detection i.e git clone

4. Convert the XML files to CSV files (the CSV files contain the width, height, depth, xmin,ymin, xmax, ymax per image)

5. Convert the csv file into tfrecords file (for train and test)

6. Download the base model from tensorflow model zoo1 (eg: ssd resnet 50fpn coco)
and unzip the file.

7. From the folder (ssd resnet 50fpn coco) open the pipeline.config file and make the changes.

8. Now open the model’s folder, open the research folder, followed by object detection folder, and open the legacy folder. In the legacy, folder opens the train.py file and start the training.

9. Once the training is completed, the results are saved in ckpt files.

10. The results of the training can be monitored on the tensor board by using the events file generated along with the ckpt files.

11. Freeze the model - Cktp have 3 files, data, index, and meta, and these three files have to be combined into one file and this is called freezing of the model.

12. From the models/research/object_detection folder opens the export_inference_graph.py. Perform the command to generate the frozen_inference_graph.pb which will be used for further inferences.

13. The frozen_inference_graph.pb, the labels.txt, and the test_video.mp4 are the final inputs on basis of which we will measure the KPI metrics.

14. Make predictions on the test images using the predict.py file

15. Tweak visualization utils to return box classes scores

16. Process the video into frames

17. Finally, run the video_processing.ipynb generate the output i.e find the KPI metrics for each brand logo.
