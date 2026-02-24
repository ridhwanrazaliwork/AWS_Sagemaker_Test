## AWS SageMaker Mobile Price Classification

Sagemaker test (mind that this is with older sagemaker v1 version)

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

**WARNING (Testing only - IAM & Networking):** Use least-privilege IAM roles and scoped policies; avoid granting broad/full access in production. Also avoid deploying resources into default/public subnets for production — prefer private subnets, NAT gateway or VPC endpoints, and properly scoped security groups.

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

---

## 🧹 Cleanup (Important: Avoid AWS Costs)

⚠️ **To prevent unexpected charges, clean up these AWS SageMaker resources after testing:**

1. **Delete SageMaker Endpoint**
   - AWS Console → SageMaker → Endpoints → Select endpoint → Delete
   - This is critical as running endpoints incur hourly charges

2. **Delete Endpoint Configuration**
   - AWS Console → SageMaker → Endpoint Configurations → Select config → Delete

3. **Delete Model**
   - AWS Console → SageMaker → Models → Select model → Delete

4. **Clean S3 Bucket**
   - AWS Console → S3 → Select bucket → Delete all training/test data and artifacts
   - Delete the bucket if created specifically for this project

5. **Remove IAM Role** (if created specifically for this project)
   - AWS Console → IAM → Roles → Select role → Delete

6. **Delete CloudWatch Logs** (optional)
   - AWS Console → CloudWatch → Logs → Delete log groups related to SageMaker

---

## References
- MLOPS Udemy course from Krish Naik