# User Guide - Blinkit Sales Analytics Dashboard

## 📖 Overview

This user guide provides comprehensive instructions for using the Blinkit Sales Analytics Dashboard. The dashboard is designed to provide actionable insights into sales performance, product analytics, and customer satisfaction metrics.

## 🎯 Dashboard Navigation

### Main Dashboard Pages

The dashboard consists of several pages, each focusing on different aspects of the business:

1. **📊 Sales Overview** - High-level sales performance metrics
2. **📦 Product Analytics** - Detailed product and category analysis  
3. **⭐ Customer Insights** - Customer satisfaction and rating analysis
4. **🏪 Outlet Performance** - Store-wise performance comparison
5. **📈 Trends & Forecasting** - Time-series analysis and projections

### Navigation Controls
- **Page Tabs**: Located at the bottom of the screen
- **Home Button**: Returns to the main overview page
- **Filter Panel**: Located on the right side (collapsible)
- **Refresh Button**: Updates data from the source

## 📊 Key Performance Indicators (KPIs)

### Primary KPIs Displayed

#### 💰 Total Sales Revenue
- **Location**: Top-left KPI card
- **Description**: Sum of all sales across all outlets and time periods
- **Format**: Currency (₹)
- **Color Coding**: 
  - Green: Above target
  - Yellow: Near target  
  - Red: Below target

#### 📦 Total Items Sold
- **Location**: Top-center KPI card
- **Description**: Count of all items sold
- **Format**: Number with thousands separator
- **Drill-down**: Click to see item breakdown

#### ⭐ Average Customer Rating
- **Location**: Top-right KPI card
- **Description**: Average rating across all products and outlets
- **Format**: Decimal (1.0 - 5.0 scale)
- **Visual Indicator**: Star rating display

#### 🏪 Active Outlets
- **Location**: Additional KPI card
- **Description**: Number of operational store locations
- **Format**: Whole number
- **Status**: Updates based on current data

## 🔍 Interactive Features

### Filtering Options

#### Date Range Filter
- **Location**: Top filter bar
- **Options**: 
  - Last 7 days
  - Last 30 days
  - Last 90 days
  - Custom range
  - Year-to-date
- **Usage**: Click dropdown → Select desired range

#### Product Category Filter
- **Location**: Left sidebar
- **Categories Available**:
  - Fruits and Vegetables
  - Snacks Foods
  - Dairy Products
  - Meat and Seafood
  - Beverages
  - Household Items
- **Multi-select**: Use Ctrl+Click for multiple categories

#### Outlet Location Filter
- **Location**: Left sidebar
- **Usage**: Select specific stores or regions
- **Options**: 
  - All locations
  - Tier 1 cities
  - Tier 2 cities
  - Tier 3 cities
  - Individual store selection

#### Rating Filter
- **Location**: Filter panel
- **Range**: 1 to 5 stars
- **Usage**: Use slider or input specific values

### Visual Interactions

#### Cross-Filtering
- **How it works**: Clicking on any chart element filters other visuals
- **Example**: Click on a product category in the pie chart to filter all other charts
- **Reset**: Click the same element again or use "Clear filters"

#### Drill-Down Capabilities
- **Sales by Time**: 
  - Year → Quarter → Month → Week → Day
  - Right-click → "Drill down" or use drill buttons
- **Product Hierarchy**:
  - Category → Subcategory → Individual Items
- **Geographic Drill-down**:
  - Region → State → City → Store

#### Hover Tooltips
- **Information Displayed**:
  - Exact values
  - Percentage contributions
  - Comparative metrics
  - Additional context

## 📈 Chart Types and Interpretation

### Sales Trend Line Chart
- **Purpose**: Shows sales performance over time
- **Features**:
  - Multiple trend lines for different categories
  - Seasonal pattern identification
  - Growth rate indicators
- **Interaction**: Hover for exact values, click to drill down

### Product Performance Bar Chart
- **Purpose**: Compares performance across different products/categories
- **Features**:
  - Horizontal/vertical bar options
  - Color coding by performance
  - Data labels showing exact values
- **Sorting**: Click column headers to sort

### Geographic Heat Map
- **Purpose**: Shows performance by location
- **Features**:
  - Color intensity indicates performance level
  - Zoom capabilities
  - Store location markers
- **Usage**: Click regions for detailed view

### Rating Distribution Donut Chart
- **Purpose**: Displays customer satisfaction distribution
- **Features**:
  - Percentage breakdown by rating
  - Color-coded segments
  - Center displays average rating
- **Interaction**: Click segments to filter by rating

## 🔄 Data Refresh and Updates

### Manual Refresh
1. Click **Home** → **Refresh** in Power BI Desktop
2. Wait for data processing (typically 30-60 seconds)
3. Verify update timestamp in the corner

### Automatic Refresh (Power BI Service)
- **Schedule**: Can be set up for daily/weekly refresh
- **Requirements**: Data source must be accessible
- **Notifications**: Email alerts for refresh failures

### Data Freshness Indicator
- **Location**: Bottom-right corner
- **Format**: "Last updated: DD/MM/YYYY HH:MM"
- **Color**: Green (recent), Yellow (1+ days), Red (3+ days old)

## 🎨 Customization Options

### Visual Formatting
- **Colors**: Right-click visual → Format → Colors
- **Fonts**: Format panel → General → Text
- **Sizing**: Drag corners or use size properties

### Filter Customization
- **Default Filters**: Set in Filters panel
- **Filter Types**: Basic, Advanced, Top N
- **Visibility**: Hide/show filter panels

### Layout Modifications
- **Moving Visuals**: Click and drag to reposition
- **Resizing**: Use corner handles
- **Adding Elements**: Insert → Text box, Image, or Button

## 📋 Common Use Cases

### Weekly Sales Review
1. Set date filter to "Last 7 days"
2. Review KPI performance vs. targets
3. Check sales trend for patterns
4. Identify top/bottom performing products
5. Export key charts for presentation

### Monthly Business Review
1. Use "Last 30 days" filter
2. Compare performance to previous month
3. Analyze customer satisfaction trends
4. Review outlet performance rankings
5. Generate summary report

### Product Strategy Analysis
1. Filter by specific product categories
2. Analyze rating vs. sales correlation
3. Identify high-performing, low-rated products
4. Review geographic performance variations
5. Export detailed product data

### Customer Satisfaction Investigation
1. Filter by rating ranges (e.g., 1-2 stars)
2. Identify common issues in low-rated categories
3. Check correlation with sales volume
4. Analyze outlet-specific satisfaction patterns

## 📊 Export and Sharing

### Export Options

#### Export to Excel
1. Right-click on any visual
2. Select "Export data"
3. Choose "Underlying data" or "Summarized data"
4. Save Excel file

#### Export to PDF
1. Go to File → Export → Export as PDF
2. Select pages to include
3. Choose layout options
4. Save PDF file

#### Export to PowerPoint
1. Go to File → Export → Export as PowerPoint
2. Select dashboard pages
3. Choose slide format
4. Generate presentation

#### Export Images
1. Right-click on specific visual
2. Select "Export as image"
3. Choose format (PNG, JPG)
4. Save image file

### Sharing Dashboard

#### Share via Power BI Service
1. Publish to Power BI Service
2. Create workspace for team access
3. Set permissions (Viewer, Contributor, Admin)
4. Share via email or link

#### Print Dashboard
1. Go to File → Print
2. Select print range
3. Adjust scaling and orientation
4. Print or save as PDF

## 🛠️ Troubleshooting

### Common Issues

#### Slow Performance
**Symptoms**: Dashboard takes long to load or respond
**Solutions**:
- Reduce date range filters
- Limit number of selected categories
- Close other applications
- Check system resources

#### Blank Visuals
**Symptoms**: Charts show no data or error messages
**Solutions**:
- Check if filters are too restrictive
- Verify data source connection
- Refresh the dashboard
- Clear all filters and retry

#### Incorrect Data Display
**Symptoms**: Numbers don't match expectations
**Solutions**:
- Verify filter selections
- Check data source for recent updates
- Review calculation logic
- Compare with raw data source

## 📚 Advanced Features

### Custom Calculations
- **DAX Measures**: Create custom calculations
- **Quick Measures**: Use built-in calculation templates
- **Calculated Columns**: Add computed fields to data model

### Bookmarks
- **Save Views**: Create bookmarks for specific filter combinations
- **Quick Access**: Switch between saved analysis views
- **Presentation Mode**: Use bookmarks for guided story telling

### Q&A Feature
- **Natural Language**: Ask questions in plain English
- **Example Queries**:
  - "What were the sales last month?"
  - "Which product has the highest rating?"
  - "Show me sales by region"

## 🎯 Best Practices

### Efficient Analysis
1. **Start Broad**: Begin with overview, then drill down
2. **Use Filters**: Apply relevant filters before detailed analysis
3. **Compare Periods**: Always compare current vs. previous periods
4. **Cross-Reference**: Use multiple charts to validate insights
5. **Document Findings**: Export key insights for future reference

### Performance Tips
1. **Limit Data Range**: Use appropriate time ranges for analysis
2. **Progressive Filtering**: Apply filters step by step
3. **Regular Refresh**: Keep data current for accurate insights
4. **Efficient Navigation**: Use bookmarks for frequently accessed views

## 📞 Getting Help

### Built-in Help
- **Tooltips**: Hover over icons for explanations
- **Help Menu**: Access Power BI help documentation
- **Sample Queries**: Use Q&A suggested questions

### External Resources
- **Documentation**: Check `documentation/` folder for additional guides
- **GitHub Issues**: Report problems or request features
- **Community**: Join Power BI user community for tips and tricks

---

**Next Steps**: For technical setup information, see [SETUP.md](SETUP.md). For data structure details, review [DATA_SCHEMA.md](DATA_SCHEMA.md).