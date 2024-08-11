

# License Plate Detector


![Screenshot 2024-08-11 184846](https://github.com/user-attachments/assets/ab21312f-6dde-4b69-89b9-da19c4b86c4c)
![Screenshot 2024-08-11 185027](https://github.com/user-attachments/assets/e09d1a92-1a8f-4e1b-8579-efae8d63fb5d)


## Overview
The **License Plate Detector** is an OpenCV-based project that detects license plates in real-time using a webcam. This project uses the Haar Cascade classifier, specifically trained for Russian license plates, to identify and extract license plates from the video feed.

## Features
- **Real-Time Detection**: Detects license plates in real-time using a webcam feed.
- **Plate Extraction**: Crops and saves the detected license plates as images for further processing.
- **Visual Feedback**: Draws rectangles around detected plates in the video feed for visual verification.

## Prerequisites
Before running the project, ensure you have the following:
- **OpenCV**: Installed and configured in your development environment.
- **Haar Cascade XML File**: The `haarcascade_russian_plate_number.xml` file for detecting license plates.

## Setup

1. **Clone the Repository**:
    ```bash
    git clone <repository-url>
    cd License-Plate-Detector
    ```

2. **Download the Haar Cascade File**:
   - Download the `haarcascade_russian_plate_number.xml` file from [OpenCV GitHub repository](https://github.com/opencv/opencv/tree/master/data/haarcascades).
   - Place it in the `Resources` folder within the project directory.

3. **Create a Directory for Saved Plates**:
   - Ensure you have a directory named `Plates` inside the `Resources` folder where the detected plates will be saved.

4. **Build the Project**:
   - Compile the code using your preferred C++ compiler, making sure to link the OpenCV libraries.

## Usage

1. **Run the Project**:
   - Execute the compiled program to start the webcam feed.
   - The program will automatically detect and highlight license plates in the video feed.

2. **View Detected Plates**:
   - Detected license plates will be saved as images in the `Resources/Plates/` directory.

## Code Explanation

The main parts of the project code include:

- **Loading Haar Cascade**:
  ```cpp
  plateCascade.load("Resources/haarcascade_russian_plate_number.xml");
  if (plateCascade.empty()) { cout << "XML file not loaded" << endl; }
  ```

- **Detecting License Plates**:
  ```cpp
  plateCascade.detectMultiScale(img, plates, 1.1, 10);
  ```

- **Drawing Rectangles Around Plates**:
  ```cpp
  rectangle(img, plates[i].tl(), plates[i].br(), Scalar(255, 0, 255), 3);
  ```

- **Saving Detected Plates**:
  ```cpp
  imwrite("Resources/Plates/" + to_string(i) + ".png", imgCrop);
  ```

## Customization
- **Different Cascades**: You can experiment with different Haar Cascade files for detecting other objects.
- **Adjusting Detection Sensitivity**: Modify the `detectMultiScale` parameters (`scaleFactor`, `minNeighbors`) to fine-tune the detection.

## Contributing
Feel free to fork the project and submit pull requests if you have any improvements or bug fixes.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements
- **OpenCV**: For providing the powerful library that made this project possible.
- **Haar Cascades**: For offering pre-trained classifiers for various object detection tasks.
