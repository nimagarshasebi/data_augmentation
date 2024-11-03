Data Augmentation on DOTA v1.5 Dataset
This repository contains implementations of Mosaic and Cutout data augmentation techniques, applied to the DOTA v1.5 dataset. These augmentations are useful for enhancing the variability of images, which helps to improve model robustness and performance during training.

1. Mosaic Data Augmentation
The Mosaic augmentation combines four images from the dataset into a single image by placing them in four quadrants. The image with the highest object density is used as the largest quadrant, with the other images filling the remaining areas. This augmentation is particularly effective for creating images with diverse object arrangements.

Code Overview
Calculate Density: The calculate_density function identifies the image with the highest density (based on annotation count) to be used as the primary quadrant in the mosaic.
Mosaic Creation: The mosaic_augmentation function creates a blank 3000x3000 canvas, places the densest image in the largest quadrant, and fills the other quadrants with the remaining images.
Annotation Handling: Annotations are adjusted to correspond to the new positions of objects within the mosaic image.
Example
Input Images:

![aaaa](https://github.com/user-attachments/assets/0e8a641f-a4db-4361-8205-505a9460dcdc)


Output Mosaic Image:

![dddd](https://github.com/user-attachments/assets/7178c623-8026-4a33-9566-b31ba17e70bc)





2. Cutout Data Augmentation
The Cutout augmentation technique involves creating random square cutouts on an image to mask parts of the objects. In addition to modifying the image, the method updates annotations to remove any objects that overlap with the masked region.

Code Overview
Load Image and Labels: The load_image_and_labels function reads the image and its corresponding annotations, mapping each annotation to a class using a label dictionary.
Cutout Application: The cutout function applies a square mask at a random location on the image. Annotations for objects within the masked area are removed to prevent mislabeling.
Annotation Drawing: The draw_annotations function draws the remaining annotations on the image, making it easy to visualize which annotations were kept after cutout.
Example
Input Image:

![P0005 copy](https://github.com/user-attachments/assets/64a5d6d3-1f39-4e9a-b924-4ba732297da2)


Output Cutout Image with Updated Annotations:

![P0005 copy](https://github.com/user-attachments/assets/152350b6-6bed-46a8-adee-0efd1f5c841f)

Running the Augmentations
To run each augmentation, place your images and labels in the appropriate folders and specify the paths in the provided script. Adjust parameters (e.g., the number of cutouts, dimensions) as needed for your dataset requirements.
