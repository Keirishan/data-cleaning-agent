# Data Cleaning Agent - Project Configuration

## Project Overview
**Project Name**: Automated Data Cleaning and Preprocessing Agent  
**Version**: 1.0.0  
**Purpose**: Automate data cleaning and preprocessing workflows for ML/AI model development  
**Last Updated**: August 30, 2025

## Workflow Definition

### Phase 1: Dataset Validation and Discovery
**Objective**: Verify dataset existence and understand data structure

**Steps**:
1. **File Existence Check**
   - Verify dataset file exists in `/dataset_original` folder
   - Validate file format compatibility
   - Check file accessibility and permissions
   - Document file size and basic metadata

2. **Initial Data Loading**
   - Load dataset using appropriate pandas/library methods
   - Handle encoding issues (UTF-8, Latin-1, etc.)
   - Capture loading errors and warnings
   - Create initial data snapshot

3. **Basic Data Profiling**
   - Generate dataset shape (rows, columns)
   - Identify data types for each column
   - Calculate memory usage
   - Create initial data sample preview

**Expected Outputs**: 
- Dataset validation report
- Initial data profile summary
- Loading script (`01_data_loading.py`)

### Phase 2: Data Quality Assessment
**Objective**: Comprehensive analysis of data quality issues

**Steps**:
1. **Missing Data Analysis**
   - Calculate missing value percentages per column
   - Identify missing data patterns (MCAR, MAR, MNAR)
   - Create missing data visualization
   - Assess impact on target variables

2. **Duplicate Detection**
   - Identify exact duplicates
   - Find near-duplicates using similarity metrics
   - Analyze duplicate patterns and potential causes
   - Estimate data redundancy levels

3. **Data Type Validation**
   - Verify expected vs actual data types
   - Identify inconsistent formats
   - Detect mixed data types in columns
   - Flag potential conversion issues

4. **Outlier Detection**
   - Statistical outlier identification (Z-score, IQR)
   - Domain-specific outlier detection
   - Multivariate outlier analysis
   - Assess outlier impact on distributions

5. **Data Consistency Checks**
   - Cross-field validation rules
   - Business logic violations
   - Referential integrity issues
   - Format standardization needs

**Expected Outputs**:
- Data quality report (`data_quality_report.html`)
- Quality assessment script (`02_quality_assessment.py`)
- Visualization files (`/plots` folder)

### Phase 3: Cleaning Strategy Development
**Objective**: Design tailored cleaning approach based on assessment

**Steps**:
1. **Prioritize Issues**
   - Rank quality issues by severity and impact
   - Consider domain requirements and constraints
   - Assess resource requirements for each fix
   - Define success criteria

2. **Strategy Selection**
   - Choose appropriate missing value strategies
   - Select outlier treatment methods
   - Define data type conversion approaches
   - Plan duplicate resolution methods

3. **Validation Framework**
   - Design data validation rules
   - Create quality metrics and thresholds
   - Define testing procedures
   - Plan rollback strategies

**Expected Outputs**:
- Cleaning strategy document (`cleaning_strategy.md`)
- Validation framework (`03_validation_framework.py`)

### Phase 4: Data Cleaning Implementation
**Objective**: Execute cleaning operations systematically

**Steps**:
1. **Missing Value Treatment**
   - Apply selected imputation methods
   - Handle missing value indicators
   - Create imputation audit trail
   - Validate imputation quality

2. **Duplicate Resolution**
   - Remove exact duplicates
   - Resolve near-duplicates based on rules
   - Preserve data provenance
   - Document removal decisions

3. **Data Type Standardization**
   - Convert data types appropriately
   - Standardize date/time formats
   - Handle categorical variables
   - Ensure numeric precision

4. **Outlier Treatment**
   - Apply selected outlier treatment methods
   - Document outlier modifications
   - Preserve extreme value information
   - Validate distributional changes

5. **Feature Engineering (Basic)**
   - Create derived features if needed
   - Apply encoding for categorical variables
   - Normalize/scale numeric features
   - Handle datetime extractions

**Expected Outputs**:
- Cleaned dataset files (`/cleaned_data` folder)
- Cleaning implementation scripts (`04_data_cleaning.py`)
- Transformation log (`transformation_log.csv`)

### Phase 5: Quality Validation and Documentation
**Objective**: Verify cleaning results and document process

**Steps**:
1. **Post-Cleaning Validation**
   - Re-run data quality assessments
   - Compare before/after metrics
   - Validate business rules compliance
   - Check data integrity constraints

2. **Impact Analysis**
   - Measure data reduction/modification rates
   - Assess statistical property changes
   - Evaluate target variable preservation
   - Document trade-offs made

3. **Documentation Generation**
   - Create comprehensive cleaning report
   - Document methodology and decisions
   - Generate data dictionary
   - Provide usage recommendations

4. **Deliverable Preparation**
   - Package cleaned datasets
   - Organize scripts and documentation
   - Create reproducible workflow
   - Prepare handover materials

**Expected Outputs**:
- Final cleaned dataset(s)
- Comprehensive cleaning report (`final_cleaning_report.pdf`)
- Complete script package
- Data lineage documentation

## Technical Configuration

### Required Libraries
```python
# Core data manipulation
pandas >= 1.5.0
numpy >= 1.21.0

# Data quality and profiling
pandas-profiling >= 3.0.0
great-expectations >= 0.15.0

# Visualization
matplotlib >= 3.5.0
seaborn >= 0.11.0
plotly >= 5.0.0

# Missing value imputation
scikit-learn >= 1.1.0
missingno >= 0.5.0

# File handling
openpyxl >= 3.0.0
xlrd >= 2.0.0
```

### File Organization
```
/dataset_original          # Original datasets (read-only)
/processing_workspace      # Active processing area
  ├── /scripts            # Generated Python scripts
  ├── /cleaned_data       # Cleaned datasets
  ├── /reports           # Quality and cleaning reports
  ├── /plots             # Visualization outputs
  ├── /logs              # Processing logs
  └── /temp              # Temporary files
```

### Quality Thresholds
- **Missing Value Threshold**: 50% (columns with >50% missing flagged for removal)
- **Outlier Detection**: 3-sigma rule, IQR method
- **Duplicate Similarity**: 95% field match threshold
- **Memory Usage Limit**: 2GB maximum dataset size
- **Processing Timeout**: 30 minutes per phase

### Coding Standards
- **PEP 8** compliance for all generated Python code
- **Comprehensive logging** for all operations
- **Error handling** with graceful degradation
- **Modular functions** for reusability
- **Clear documentation** in code comments

## Business Rules and Constraints

### Data Preservation Rules
1. **Never modify original datasets** - always work on copies
2. **Maintain data lineage** - track all transformations
3. **Preserve critical identifiers** - customer IDs, primary keys
4. **Document all decisions** - provide audit trail
5. **Enable rollback** - maintain reversibility where possible

### Domain-Specific Considerations
- **Financial Data**: Preserve precision, handle currency formats
- **Healthcare Data**: HIPAA compliance, sensitive data handling
- **Customer Data**: PII protection, consent validation
- **Time Series**: Temporal integrity, seasonality preservation
- **Geospatial Data**: Coordinate system consistency

### Performance Requirements
- **Processing Speed**: Target 10,000 rows/second for basic operations
- **Memory Efficiency**: Chunked processing for large datasets
- **Scalability**: Support up to 10M rows, 1000 columns
- **Reliability**: 99.9% success rate for standard operations

## Validation and Testing

### Automated Tests
- **Data integrity tests** after each phase
- **Statistical validation** of transformations
- **Business rule compliance** checking
- **Performance benchmarking**
- **Error handling verification**

### Quality Gates
- Each phase must pass validation before proceeding
- Manual approval required for high-impact changes
- Rollback triggers for quality degradation
- Documentation completeness checks

## Integration Points

### Input Sources
- CSV files from various systems
- Database exports (SQL dumps)
- API data extracts
- Excel files from business users
- Cloud storage data lakes

### Output Destinations
- ML pipeline input folders
- Data warehouse staging areas
- Analytics platforms
- Business intelligence tools
- Model training environments

## Monitoring and Maintenance

### Key Metrics
- **Processing Success Rate**: % of successful cleaning operations
- **Data Quality Improvement**: Before/after quality scores
- **Processing Time**: Average time per dataset size
- **User Satisfaction**: Feedback on cleaning quality
- **Error Frequency**: Types and frequency of failures

### Maintenance Schedule
- **Weekly**: Review processing logs and error rates
- **Monthly**: Update quality thresholds based on feedback
- **Quarterly**: Review and update cleaning strategies
- **Annually**: Major version updates and capability expansion
