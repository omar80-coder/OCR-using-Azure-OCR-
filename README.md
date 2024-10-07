# Invoice Information Extraction using LayoutLMv3 and LayoutLMv2

This project aims to automate the extraction of key information from invoice documents using deep learning models, specifically LayoutLMv3 and LayoutLMv2. The project involves the following key steps:

## 1. Data Preparation

- **Image Resizing:** Invoice images are resized to a consistent size (e.g., 1000x700 pixels) and stored in the 'resized_hand' directory.
- **Annotation:**  Invoices are annotated to identify key information fields, such as invoice title, date, total amount, etc. This annotation data is saved in JSON format in the 'finaly' directory. Each annotation file contains the image filename, bounding boxes for each word, and corresponding labels (e.g., 'B-title', 'I-title', 'B-date', etc.).
- **Dataset Creation:** The project uses a custom dataset class to load the images and annotations. The dataset is split into training and testing sets. Data augmentation is applied during training to improve model robustness.


## 2. Model Training

- **LayoutLMv3/LayoutLMv2 Initialization:**  The project utilizes pre-trained LayoutLMv3 and LayoutLMv2 models from Hugging Face Transformers. 
- **Fine-tuning:** The models are fine-tuned on the training dataset to adapt them specifically for invoice information extraction. The training process involves optimizing the model's parameters to minimize a loss function, typically cross-entropy loss or a focal loss.
- **Hyperparameter Tuning:**  The training process involves adjusting hyperparameters, such as learning rate, batch size, and the number of epochs, to achieve optimal performance.
- **Early Stopping:** Early stopping is employed to prevent overfitting, halting the training process when the model's performance on a validation set starts to decrease.



## 3. Evaluation

- **Metrics:** The project uses the 'seqeval' and 'evaluate' libraries to assess the performance of the models. Key metrics include precision, recall, F1-score, and accuracy, providing insight into the model's ability to correctly identify and classify key information fields in invoices.
- **MLflow:** MLflow is utilized for experiment tracking and logging model metrics, allowing for comparison of different model configurations and hyperparameter settings.

## 4. Inference

- **Loading the Trained Model:** The fine-tuned model is loaded to perform inference on new, unseen invoice images.
- **Preprocessing:**  Input images undergo preprocessing, including resizing and potentially other transformations, to match the format expected by the model.
- **Extraction:** The model processes the image and identifies regions of interest, extracting the key information fields along with their associated labels.
- **Output:**  The extracted information is then presented in a structured format, such as a dictionary or JSON, facilitating downstream processing and integration with other systems.

## Conclusion

This project demonstrates the effectiveness of using LayoutLMv3 and LayoutLMv2 for automated invoice information extraction. The described process highlights the key steps involved in data preparation, model training, evaluation, and inference, enabling the development of a robust and accurate solution for this task.
