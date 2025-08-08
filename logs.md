Bird Classifier
To find the name of a bird with only a image
used existing dataset  http://www.vision.caltech.edu/visipedia

Approch
experiments
Results
Conclusions
Future Work

Day 01 - 22/07/2025
    understanding data by README.md, EDA, 
    what we have - 117788 images, 
        11788 bounds(id, x, y, width, height), 
        15 parts, 
        true parts loc(img_id, part_id, x, y, visible), 
        visible parts loc(img_id, part_id, x, y, visible, time), 
        312 attributes, 
        4 certainites, (not visible, guessing, probably, definitely)
        11788 image_attribute_labels(image_id, attribute_id, is_present, certainity_id, time), 
        200*312 class_attributes(% of a an attribute is assumed to be present), 
        200 species
    data is clean
APPROCH 1 - considering the visibility of a part based on the given information
APPROCH 2 - condidering the visibility of a part based on the actual time taken by people to see a part in the image

Day 02 - 23/07/2025 <=> Day 06 - 27/07/2025 
    formating the data
    image - 312 attributes, visibility, certainities, bounds, parts, parts location, parts_visibility
    starting with a simple CNN which gives a output of 312 values

Day 07 - 28/07/2025 <=> Day 08 - 29/07/2025
    training the model with the architecture
        all images are resized to 224*224
        (3, 224, 224)
        conv1 = 3, 32, kernel_size = 3, padding = 1
        maxPool = (2,2)
        conv2 = 32, 64, kernel_size = 3, padding = 1
        maxPool = (2,2)
        (64, 56, 56)
        flatten_size = 64*56*56
        fc = (flatten_size, 1024)
        fc = (1024, 512)
        fc = (512, 312)
        optimizer = Adam with learning rate = 0.001
        target lable are the ground truth of the each image

        
Day 09 - 30/07/25
    training of the previous architecture is still ongoing
    coming up with a new architecture

Day 10 - 06/08/25
    traning results : traning loss 45. and validation loss 175.

Day 11 - 07/08/25
    labels until now, all the percentages are considered which were from class_attribute_labels_continuous, 
    target label => certainity, is_present, percentage 