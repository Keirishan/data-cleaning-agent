# Data Cleaning Agent - Quick Start Guide

## 🎯 Welcome to Your Data Cleaning Agent!

This automated agent helps you clean and preprocess datasets for machine learning projects. Just place your data and describe what you need!

## 📁 Folder Structure

```
data-cleaning-agent/
├── dataset_original/          # 📥 Put your raw datasets here
├── processing_workspace/      # 🔧 Agent works here
│   ├── scripts/              # Generated Python scripts
│   ├── cleaned_data/         # Your cleaned datasets
│   ├── reports/              # Quality reports
│   └── logs/                 # Processing logs
├── instruction.md            # 📖 Detailed user guide
├── project_config.md         # ⚙️ Workflow configuration
└── workflow_status.md        # 📊 Current progress tracker
```

## 🚀 How to Start

### Step 1: Add Your Dataset
- Place your data file in the `/dataset_original` folder
- Supported formats: CSV, Excel, JSON, Parquet

### Step 2: Describe Your Needs
Send a message like this:

```
Hi Data Cleaning Agent!

Dataset Information:
- Dataset file name: sales_data.csv
- Dataset description: Monthly sales records with customer info
- Target use case: Regression analysis for sales prediction
- Specific requirements: Keep all customer IDs, handle missing values carefully
```

### Step 3: Let the Agent Work
The agent will:
1. ✅ Validate your dataset
2. 🔍 Analyze data quality issues  
3. 📋 Propose a cleaning strategy
4. 🛠️ Clean your data (with your approval)
5. 📊 Provide detailed reports

## 📊 What You'll Get

After processing, find these in `/processing_workspace`:
- **Cleaned dataset(s)** ready for ML
- **Python scripts** for reproducibility
- **Quality reports** showing improvements
- **Documentation** explaining all changes

## 🆘 Need Help?

- Check `instruction.md` for detailed guidance
- Review `workflow_status.md` to see current progress
- Look at `project_config.md` for technical details

## 🎉 Ready to Clean Your Data?

Just follow Step 2 above with your dataset information!
