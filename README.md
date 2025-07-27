# Pharmaceutical Drug Recognition

A machine learning project for recognizing and classifying pharmaceutical drugs using computer vision techniques. This project includes data preprocessing, model training, and multiple deployment formats for different platforms.

## Overview

This project implements a convolutional neural network (CNN) to classify pharmaceutical drugs from images. The model is trained to recognize different types of medications and can be deployed in various formats including web applications, mobile apps, and embedded systems.
<img width="778" height="989" alt="image" src="https://github.com/user-attachments/assets/8cc28737-b4f2-431a-96f5-6d57e44b1096" />


## Features

- Image preprocessing and data augmentation
- CNN model training with TensorFlow/Keras
- Model evaluation and performance metrics
- Multiple deployment formats:
  - TensorFlow SavedModel
  - TensorFlow Lite (for mobile/edge devices)
  - TensorFlow.js (for web applications)
- Comprehensive data analysis and visualization

## Dataset Classes

The model can classify the following pharmaceutical drugs:
- **Alaxan** - Anti-inflammatory medication
- **Bactidol** - Antiseptic mouthwash
- **Bioflu** - Cold and flu medication
- **Biogesic** - Pain reliever and fever reducer
- **DayZinc** - Zinc supplement
- **Decolgen** - Decongestant medication
- **Fish Oil** - Omega-3 supplement
- **Kremil S** - Antacid medication
- **Medicol** - Pain reliever
- **Neozep** - Cold medication

## Visualizations

### Sample Drug Images by Category
The dataset contains synthetic images of various pharmaceutical products. Each category shows distinct visual characteristics that help the model learn to distinguish between different medications.

### Model Performance Visualization
The training process includes comprehensive visualization of:
- **Training vs Validation Accuracy**: Shows model learning progression over epochs
- **Training vs Validation Loss**: Demonstrates convergence and potential overfitting
- **Confusion Matrix**: Detailed breakdown of classification performance per drug category
- **Classification Report**: Precision, recall, and F1-scores for each drug class

### Prediction Examples
The model provides confidence scores for each prediction, displaying:
- Original drug image
- Predicted drug class with confidence percentage
- Probability distribution across all 10 drug categories
- Color-coded results (blue for correct predictions, red for incorrect)

### Data Distribution
Bar charts showing the number of training samples per drug category, ensuring balanced representation across all pharmaceutical classes.

## Project Structure

```
pharmactical-drug-recognition-main/
├── notebook.ipynb          # Main Jupyter notebook with complete workflow
├── requirements.txt        # Python dependencies
├── 00000033.jpg           # Sample drug image
├── saved_model/           # TensorFlow SavedModel format
├── tflite/               # TensorFlow Lite model files
├── tfjs_model/           # TensorFlow.js model files
└── README.md             # This file
```

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd pharmactical-drug-recognition-main
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install required dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Training the Model

1. Open the Jupyter notebook:
```bash
jupyter notebook notebook.ipynb
```

2. Run all cells in the notebook to:
   - Load and preprocess the dataset
   - Visualize data distribution and sample images
   - Apply data augmentation techniques
   - Train the CNN model with MobileNet backbone
   - Generate performance visualizations
   - Evaluate model performance with confusion matrix
   - Export models in different formats

### Visualization Features in Notebook

The notebook includes several visualization components:

1. **Dataset Overview**: Random sample images from each drug category
2. **Data Distribution**: Bar chart showing image counts per class
3. **Training Progress**: Real-time plots of accuracy and loss curves
4. **Model Evaluation**: Confusion matrix heatmap and classification metrics
5. **Prediction Examples**: Side-by-side comparison of images with prediction probabilities

### Using Pre-trained Models

#### TensorFlow SavedModel
```python
import tensorflow as tf

# Load the saved model
model = tf.keras.models.load_model('saved_model/')

# Make predictions
predictions = model.predict(your_image_data)
```

#### TensorFlow Lite
```python
import tensorflow as tf

# Load TFLite model
interpreter = tf.lite.Interpreter(model_path='tflite/model.tflite')
interpreter.allocate_tensors()

# Get input and output tensors
input_details = interpreter.get_input_details()
output_details = interpreter.get_output_details()

# Make prediction
interpreter.set_tensor(input_details[0]['index'], input_data)
interpreter.invoke()
output_data = interpreter.get_tensor(output_details[0]['index'])
```

#### TensorFlow.js
```javascript
// Load the model in a web application
const model = await tf.loadLayersModel('tfjs_model/model.json');

// Make predictions
const prediction = model.predict(imageData);
```

## Model Performance

The trained model achieves excellent performance across all drug categories:
- **Training accuracy**: 95.85%
- **Validation accuracy**: 95.45%
- **Test accuracy**: 96%

### Detailed Performance Metrics
- High precision and recall across all 10 drug categories
- Robust performance on synthetic pharmaceutical images
- Effective generalization to unseen test data
- Minimal overfitting with proper regularization

## Dataset

The project uses the "Pharmaceutical Drugs and Vitamins Synthetic Images" dataset containing high-quality synthetic images of common Philippine medications. The dataset includes:
- 10 different drug categories
- Balanced distribution across classes
- High-resolution images suitable for computer vision tasks
- Consistent lighting and background conditions

Sample images like `00000033.jpg` demonstrate the input format expected by the model (224x224 RGB images).

## Model Architecture

The model uses a **MobileNet** backbone with custom classification layers:
- Pre-trained MobileNet for feature extraction
- Additional convolutional layers for domain-specific features
- Global Average Pooling for dimensionality reduction
- Dropout regularization to prevent overfitting
- Dense layers with softmax activation for classification

## Dependencies

Key dependencies include:
- TensorFlow/Keras for deep learning
- NumPy and Pandas for data manipulation
- Matplotlib and Seaborn for visualization
- PIL/OpenCV for image processing
- Scikit-learn for evaluation metrics

See `requirements.txt` for the complete list of dependencies.

## Deployment Options

### Mobile Applications
Use the TensorFlow Lite model (`tflite/`) for Android and iOS applications with optimized inference speed.

### Web Applications
Deploy the TensorFlow.js model (`tfjs_model/`) for browser-based inference without server dependencies.

### Server Applications
Use the SavedModel format (`saved_model/`) for server-side predictions with full model capabilities.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## Acknowledgments

- TensorFlow team for the machine learning framework
- Kaggle for hosting the pharmaceutical drugs dataset
- MobileNet authors for the efficient CNN architecture
- Open source community for various tools and libraries

## Contact

**Author**: Filza Rahma Muflihah  
**Email**: filzarahmamuflihah@gmail.com  
**Dicoding ID**: filza_rahma_muflihah

---

For detailed implementation, training process, and comprehensive visualizations, refer to the `notebook.ipynb` file.
