# Data Schema Documentation - Blinkit Sales Analytics Dashboard

## 📊 Overview

This document provides detailed information about the data structure, schema, and field definitions used in the Blinkit Sales Analytics Dashboard. Understanding the data schema is essential for data analysts, developers, and users who need to work with the underlying data or create custom analysis.

## 📁 Data Source Information

### Primary Data Source
- **File**: `data/BlinkIT Grocery Data.xlsx`
- **Format**: Microsoft Excel (.xlsx)
- **Encoding**: UTF-8
- **Size**: ~581 KB
- **Last Updated**: [Dynamically updated based on file timestamp]

### Data Refresh Frequency
- **Manual**: On-demand refresh via Power BI Desktop
- **Automatic**: Can be configured for scheduled refresh in Power BI Service
- **Recommended**: Daily refresh for optimal data currency

## 📋 Data Tables Schema

### Main Sales Data Table

#### Table Name: `SalesData` (Sheet: "Sales_Data")

| Column Name | Data Type | Format | Nullable | Description | Example Values |
|-------------|-----------|---------|----------|-------------|----------------|
| `Item_Identifier` | Text | String | No | Unique identifier for each product | "FDA15", "DRC01", "FDN15" |
| `Item_Weight` | Number | Decimal (2) | Yes | Weight of the product in kg | 9.30, 5.92, 17.50 |
| `Item_Fat_Content` | Text | String | No | Fat content category | "Low Fat", "Regular" |
| `Item_Visibility` | Number | Decimal (6) | No | Visibility percentage in store | 0.016047, 0.019278, 0.016760 |
| `Item_Type` | Text | String | No | Category/type of the product | "Dairy", "Soft Drinks", "Meat" |
| `Item_MRP` | Currency | Decimal (2) | No | Maximum Retail Price in ₹ | 249.8092, 48.2692, 141.618 |
| `Outlet_Identifier` | Text | String | No | Unique identifier for outlet | "OUT049", "OUT018", "OUT049" |
| `Outlet_Establishment_Year` | Number | Year | No | Year outlet was established | 1999, 2009, 1999 |
| `Outlet_Size` | Text | String | Yes | Size category of the outlet | "Medium", "Small", "High" |
| `Outlet_Location_Type` | Text | String | No | Location type of outlet | "Tier 1", "Tier 2", "Tier 3" |
| `Outlet_Type` | Text | String | No | Type of outlet | "Supermarket Type1", "Grocery Store" |
| `Item_Outlet_Sales` | Currency | Decimal (2) | No | Sales amount for item at outlet | 3735.1380, 443.4228, 2097.270 |

### Customer Rating Data Table (Optional Enhancement)

#### Table Name: `CustomerRatings` (Sheet: "Rating_Data")

| Column Name | Data Type | Format | Nullable | Description | Example Values |
|-------------|-----------|---------|----------|-------------|----------------|
| `Rating_ID` | Text | String | No | Unique rating identifier | "R001", "R002", "R003" |
| `Item_Identifier` | Text | String | No | Links to SalesData table | "FDA15", "DRC01", "FDN15" |
| `Outlet_Identifier` | Text | String | No | Links to SalesData table | "OUT049", "OUT018", "OUT049" |
| `Customer_Rating` | Number | Integer | No | Rating scale 1-5 | 4, 5, 3, 2, 1 |
| `Review_Date` | Date | Date | No | Date of rating/review | 2023-01-15, 2023-02-20 |
| `Review_Text` | Text | Long Text | Yes | Customer review comments | "Great product quality" |

## 🔗 Data Relationships

### Primary Keys and Foreign Keys

#### Primary Relationships
- **SalesData**: `Item_Identifier` + `Outlet_Identifier` (Composite Primary Key)
- **CustomerRatings**: `Rating_ID` (Primary Key)

#### Foreign Key Relationships
```
CustomerRatings.Item_Identifier → SalesData.Item_Identifier
CustomerRatings.Outlet_Identifier → SalesData.Outlet_Identifier
```

### Relationship Cardinality
- **SalesData to CustomerRatings**: One-to-Many (1:M)
- **Outlet to Sales**: One-to-Many (1:M)
- **Item to Sales**: One-to-Many (1:M)

## 📊 Data Quality Standards

### Data Validation Rules

#### Required Fields (Non-Nullable)
- `Item_Identifier`: Must be unique within each outlet
- `Item_Fat_Content`: Must be "Low Fat" or "Regular"
- `Item_Type`: Must match predefined categories
- `Outlet_Identifier`: Must be valid outlet code
- `Item_Outlet_Sales`: Must be positive number

#### Data Type Constraints
- **Dates**: Must be in YYYY-MM-DD format
- **Numbers**: Must be within logical ranges
- **Text**: Must not exceed specified character limits
- **Currency**: Must be positive values

#### Business Logic Validations
- `Item_Visibility`: Must be between 0 and 1 (percentage)
- `Customer_Rating`: Must be integer between 1 and 5
- `Outlet_Establishment_Year`: Must be between 1985 and current year
- `Item_MRP`: Must be greater than 0

### Data Cleansing Applied

#### Common Data Issues Resolved
1. **Missing Values**: 
   - `Item_Weight`: Filled with category averages
   - `Outlet_Size`: Imputed based on outlet type patterns

2. **Inconsistent Formatting**:
   - Standardized text casing for categorical fields
   - Normalized number formats and decimal places
   - Unified date formats across all date fields

3. **Outlier Detection**:
   - Sales values beyond 3 standard deviations flagged
   - Unusual item weights investigated and corrected

## 📈 Calculated Fields and Measures

### DAX Measures Created

#### Sales Metrics
```dax
Total Sales = SUM(SalesData[Item_Outlet_Sales])
Average Sales = AVERAGE(SalesData[Item_Outlet_Sales])
Sales Growth % = 
    VAR CurrentSales = [Total Sales]
    VAR PreviousSales = CALCULATE([Total Sales], DATEADD('Calendar'[Date], -1, YEAR))
    RETURN DIVIDE(CurrentSales - PreviousSales, PreviousSales, 0)
```

#### Product Metrics
```dax
Total Items = DISTINCTCOUNT(SalesData[Item_Identifier])
Average Item Price = AVERAGE(SalesData[Item_MRP])
Top Selling Item = 
    CALCULATE(
        VALUES(SalesData[Item_Identifier]),
        TOPN(1, SalesData, [Total Sales], DESC)
    )
```

#### Outlet Metrics
```dax
Active Outlets = DISTINCTCOUNT(SalesData[Outlet_Identifier])
Average Outlet Sales = DIVIDE([Total Sales], [Active Outlets], 0)
Outlet Performance Rank = RANKX(ALL(SalesData[Outlet_Identifier]), [Total Sales], , DESC)
```

#### Customer Metrics (if rating data available)
```dax
Average Rating = AVERAGE(CustomerRatings[Customer_Rating])
Rating Count = COUNT(CustomerRatings[Rating_ID])
Satisfaction Score = [Average Rating] / 5 * 100
```

### Calculated Columns

#### Date Calculations
```dax
Year = YEAR(SalesData[Transaction_Date])
Month = FORMAT(SalesData[Transaction_Date], "MMMM")
Quarter = "Q" & QUARTER(SalesData[Transaction_Date])
Week Number = WEEKNUM(SalesData[Transaction_Date])
```

#### Categorization Columns
```dax
Price Category = 
    SWITCH(
        TRUE(),
        SalesData[Item_MRP] <= 50, "Low",
        SalesData[Item_MRP] <= 150, "Medium",
        SalesData[Item_MRP] <= 300, "High",
        "Premium"
    )

Sales Performance = 
    IF(SalesData[Item_Outlet_Sales] > [Average Sales], "Above Average", "Below Average")
```

## 🏗️ Data Model Architecture

### Star Schema Design

#### Fact Table
- **SalesData**: Central fact table containing sales transactions

#### Dimension Tables
- **Items**: Product-related attributes
- **Outlets**: Store-related information  
- **Time**: Date hierarchy for time-based analysis
- **Geography**: Location-based groupings

### Model Relationships Diagram
```
     Items
       |
       | (1:M)
       |
  SalesData ←— (M:1) —→ Outlets
       |
       | (M:1)
       |
     Time
```

## 📊 Data Usage Guidelines

### Best Practices for Analysis

#### Performance Optimization
1. **Filtering**: Always apply date filters to limit data scope
2. **Aggregation**: Use appropriate aggregation levels for analysis
3. **Indexing**: Key columns are indexed for faster queries
4. **Partitioning**: Large datasets may benefit from date partitioning

#### Data Interpretation
1. **Context Awareness**: Consider seasonal patterns and business context
2. **Granularity**: Choose appropriate level of detail for analysis
3. **Validation**: Cross-check results with business knowledge
4. **Documentation**: Document assumptions and calculation methods

### Common Analysis Patterns

#### Time-Series Analysis
- Use consistent date ranges for comparison
- Account for seasonality in retail data
- Apply appropriate time grain (daily, weekly, monthly)

#### Product Analysis
- Segment by item type and price category
- Consider product lifecycle stages
- Analyze cross-selling opportunities

#### Geographic Analysis
- Compare performance across outlet types
- Consider demographic factors by location
- Analyze market penetration by tier

## 🔄 Data Maintenance

### Regular Maintenance Tasks

#### Weekly Tasks
- [ ] Validate data completeness
- [ ] Check for new outlets or products
- [ ] Review data quality metrics
- [ ] Update calculated measures if needed

#### Monthly Tasks
- [ ] Archive old data if required
- [ ] Update business rules and validations
- [ ] Review and optimize data model performance
- [ ] Document any schema changes

#### Quarterly Tasks
- [ ] Comprehensive data audit
- [ ] Update data dictionary
- [ ] Review and optimize DAX calculations
- [ ] Plan for schema evolution

### Data Backup and Recovery
- **Backup Frequency**: Daily automated backups
- **Retention Period**: 12 months of historical data
- **Recovery Process**: Documented restoration procedures
- **Testing**: Monthly backup restoration tests

## 📞 Data Support

### Data Issues Resolution

#### Common Data Problems
1. **Missing Data**: Contact data source team for investigation
2. **Data Accuracy**: Validate with business stakeholders
3. **Performance Issues**: Review query optimization
4. **Schema Changes**: Follow change management process

#### Escalation Process
1. **Level 1**: Dashboard user or analyst
2. **Level 2**: Data administrator or BI developer  
3. **Level 3**: Data engineering team
4. **Level 4**: Business stakeholders and IT management

### Contact Information
- **Data Issues**: Create GitHub issue with "data" label
- **Schema Questions**: Review documentation or contact repository maintainer
- **Enhancement Requests**: Submit feature request via GitHub

---

**Related Documentation**: 
- [Setup Guide](SETUP.md) - For installation and configuration
- [User Guide](USER_GUIDE.md) - For dashboard usage instructions