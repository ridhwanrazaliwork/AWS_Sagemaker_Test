## AWS SageMaker Mobile Price Classification

Sagemaker test (mind that this is with older v1 sagemaker)

### Project Overview

This project builds a machine learning pipeline to classify mobile phone prices into different ranges using AWS SageMaker. The workflow includes:

- **Data Preparation**: Load and split data using scikit-learn
- **Data Storage**: Upload training/testing data to Amazon S3
- **Model Training**: Train RandomForest classifier using SageMaker's SKLearn container
- **Model Deployment**: Deploy trained model as a real-time inference endpoint
- **Predictions**: Make predictions using the deployed endpoint
- **Cleanup**: Delete endpoints to avoid unnecessary charges

### Dataset

- **File**: `mob_price_classification_train.csv`
- **Task**: Multi-class classification (predicting price_range)
- **Features**: 20 mobile phone specifications
- **Train/Test Split**: 85% training, 15% testing

### Requirements

- AWS Account with SageMaker access
- IAM role with SageMaker permissions
- Python 3.x with dependencies in `requirements.txt`
- S3 bucket for storing training data

### Key Components

1. **research.ipynb** - Main notebook containing the complete SageMaker workflow
2. **script.py** - Training script executed by SageMaker
3. **train-V-1.csv** - Training dataset
4. **test-V-1.csv** - Testing dataset

### Usage

Run the cells in `research.ipynb` to:
1. Load and explore the dataset
2. Split data into train/test sets
3. Upload data to S3
4. Train a RandomForest model on SageMaker
5. Deploy the model to an endpoint
6. Make predictions on test data
7. Clean up resources

### Model Performance

The RandomForest classifier is trained with:
- **n_estimators**: 100
- **random_state**: 0
- **Evaluation**: Accuracy score and classification report on test data (15% of dataset)

## References
- MLOPS Udemy course from Krish Naik