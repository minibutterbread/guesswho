paths.py: 2 function, image path generator. Use for extracting image path from given directory.

video_to_frame.py: store every 5th frame from video clip.

click_and_crop.py: save cropped rectangle area mouse has been dragged.

annotation.py: left click on mouse, drag a rectangle area, release.  Press 'r' if reset is need. Press 'q' to skip image  Press 'a' to label object. A window will pop out asking'what obj do you want to label' **NOT GOOD, Labelimg is a much better tool**

move_image.py: copy all images that were annotated to a seperate folder as our dataset. (from orginal image folder generated by video_to_frame)



fourconlayer_model.py: structure borrowed from Simposon Recognization.

pretrainVGG16: last feature map on VGG16 have the output shape 4,4,512,  flatten it and add two dense layer as our customized classifer for our dataset.

muticlass_predit_all.py: feed in a batch of test images, and predict them all. visualization of the results.

test_over_sample.py:  test time augmentation, crop 4 corners and center of test image, add on horizontal flip, and average the predicted possibilities.  this technique only limited to classfication part, since training&test images in classficiation are occupying mian part of image, cropped image still reserved enough information. however, in detection part, obj may only at a small potion of the image. Cropping doesn't make any sense.

generate_xml.py: write in pascal voc format. use for store predicted object and predicted bounding box as annotation. Re-feed it into training data for increasing dataset.

test_yolo.py:(minor change on test.py gaven by darkflow) add write_xml function to store predited label and location.

Result: 94% f1 score. 11class with ~20image per class, ~8 test image.  test image and train image are cropped from same video, so under similar light condition, similar background.
