
# Image Processing with Bilateral Filtering and CLAHE Enhancement

## Description

This project demonstrates image enhancement using two key techniques:
1. **Bilateral Filtering**: This is an edge-preserving filter used to smooth images while keeping the edges sharp. It is particularly useful for noise reduction in images.
2. **CLAHE (Contrast Limited Adaptive Histogram Equalization)**: This technique improves the contrast of an image by applying adaptive histogram equalization to the image's L-channel in the LAB color space.

The code applies both techniques to an image and then displays the original, filtered, and enhanced versions side by side for comparison.

## Requirements

To run the script, you'll need to have the following Python libraries installed:

- OpenCV (`cv2`): For image processing tasks such as bilateral filtering and color space conversion.
- NumPy: For handling image arrays.
- Matplotlib: For displaying the images.
- scikit-image: For loading sample images from the `skimage` library.

You can install these dependencies using `pip`:

```bash
pip install opencv-python numpy matplotlib scikit-image
```

## Code Explanation

### `filter_image(img)`
This function applies a **bilateral filter** to the input image to reduce noise while preserving edges. The function uses OpenCV's `cv2.bilateralFilter()` method, with parameters `d=9`, `sigmaColor=75`, and `sigmaSpace=75`.

- `d=9`: Diameter of the pixel neighborhood.
- `sigmaColor=75`: Filter's sigma in color space.
- `sigmaSpace=75`: Filter's sigma in coordinate space.

### `enhance_image_clahe(img)`
This function enhances the contrast of the image using **CLAHE** (Contrast Limited Adaptive Histogram Equalization).

- First, it converts the image to the **LAB** color space using `cv2.cvtColor()`.
- Then, the L-channel (luminance) is extracted and enhanced using CLAHE with a clip limit of `3.0` and a tile grid size of `(8, 8)`.
- Finally, the enhanced L-channel is merged with the unchanged a and b channels, and the result is converted back to BGR color space.

### `display_results(original, filtered, enhanced)`
This function uses Matplotlib to display three versions of the image:
1. **Original Image**
2. **Filtered Image** (after applying bilateral filtering)
3. **Enhanced Image** (after applying CLAHE)

Each image is displayed side by side for easy comparison.

### Main Function
1. A sample image (the astronaut image from `skimage`) is loaded using `data.astronaut()`.
2. The `filter_image()` function is called to apply bilateral filtering.
3. The `enhance_image_clahe()` function is called to apply CLAHE enhancement.
4. The results are displayed using `display_results()`.

## How to Run

1. Make sure you have installed all the required dependencies (`opencv-python`, `numpy`, `matplotlib`, `scikit-image`).
2. Save the code in a Python script, for example, `image_processing.py`.
3. Run the script:

```bash
python image_processing.py
```

The script will process the sample image (`astronaut`), apply the bilateral filter and CLAHE enhancement, and display the results in a graphical window.

## Example Output

The output will show three images:

1. **Original Image**: The unprocessed input image.
2. **Filtered Image**: The image after bilateral filtering, with edges preserved and noise reduced.
3. **Enhanced Image (CLAHE)**: The image after contrast enhancement using CLAHE, making the image more visually distinct in terms of brightness and detail.

## Customization

- **Input Image**: Currently, the code uses a sample image (`data.astronaut()`) from `skimage`. You can replace this with your own image by loading it with `cv2.imread('your_image.jpg')` instead of using `data.astronaut()`.
  
- **Filter Settings**: You can modify the bilateral filter's parameters (`d`, `sigmaColor`, `sigmaSpace`) in the `filter_image()` function to adjust the smoothing effect.

- **CLAHE Settings**: You can also adjust the `clipLimit` and `tileGridSize` in the `enhance_image_clahe()` function to change the contrast enhancement behavior.

## License

This code is provided for educational purposes and can be freely used, modified, and distributed.
