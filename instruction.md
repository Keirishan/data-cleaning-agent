# Data Cleaning Agent - User Instructions

## Overview
This agentic workflow automates data cleaning and preprocessing tasks for ML/AI model development. The agent follows a structured, step-by-step approach based on established data cleaning principles and techniques.

## How to Use This Agent

### 1. Preparation
- Place your original dataset file in the `/dataset_original` folder
- Ensure the dataset is in a supported format (.csv, .xlsx, .json, .parquet)
- Keep a backup of your original data for safety

### 2. Initiating the Workflow
When you want to start the data cleaning process, provide the following information in your prompt:

```
Dataset Information:
- Dataset file name: [your_dataset_filename.ext]
- Dataset description: [brief description of your data]
- Target use case: [classification/regression/clustering/etc.]
- Specific requirements: [any special requirements or constraints]
```

### 3. Agent Response Pattern
The agent will respond step by step, following the defined workflow:

1. **Dataset Validation**: Confirms file existence and basic properties
2. **Initial Assessment**: Analyzes data structure, types, and quality
3. **Cleaning Strategy**: Proposes a tailored cleaning approach
4. **Implementation**: Executes cleaning steps with explanations
5. **Validation**: Verifies results and provides summary
6. **Documentation**: Creates comprehensive cleaning report

### 4. Interactive Process
- The agent will ask for clarification when needed
- You can request modifications to the cleaning strategy
- Each step will be explained before execution
- Progress will be tracked and documented

### 5. Expected Outputs
After completion, you'll find in the `/processing_workspace` folder:
- Cleaned dataset(s)
- Python scripts used for cleaning
- Data quality reports
- Cleaning documentation
- Processing logs

## Example Usage

```
Hi Data Cleaning Agent,

I need help cleaning my customer dataset for a churn prediction model.

Dataset Information:
- Dataset file name: customer_data.csv
- Dataset description: Customer demographics and transaction history
- Target use case: Binary classification (churn prediction)
- Specific requirements: Must preserve customer IDs, handle missing values conservatively
```

## Agent Capabilities

### Data Quality Issues Handled:
- Missing values (multiple imputation strategies)
- Duplicate records
- Data type inconsistencies
- Outlier detection and treatment
- Feature scaling and normalization
- Categorical variable encoding
- Date/time formatting
- Text data cleaning

### Supported File Formats:
- CSV (.csv)
- Excel (.xlsx, .xls)
- JSON (.json)
- Parquet (.parquet)
- TSV (.tsv)

### Output Formats:
- Cleaned CSV files
- Python cleaning scripts
- Jupyter notebooks (optional)
- Data profiling reports
- Quality assessment summaries

## Best Practices

1. **Always backup your original data** before starting
2. **Review the proposed cleaning strategy** before approval
3. **Provide context about your data** for better results
4. **Specify your target ML task** for appropriate preprocessing
5. **Check the generated reports** to understand changes made

## Troubleshooting

If you encounter issues:
- Ensure your dataset is in the correct folder
- Check file permissions
- Verify file format compatibility
- Review error messages in the processing logs

## Support
For additional help or custom requirements, refer to the `project_config.md` for detailed workflow specifications.
