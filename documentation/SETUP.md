# Setup Guide - Blinkit Sales Analytics Dashboard

## 📋 Prerequisites

Before setting up the Blinkit Sales Analytics Dashboard, ensure you have the following requirements:

### System Requirements
- **Operating System**: Windows 10 (version 1809 or later) or Windows 11
- **RAM**: Minimum 4GB, Recommended 8GB or higher
- **Storage**: At least 1GB free space for installation and data processing
- **Display**: 1366 x 768 resolution or higher

### Software Requirements
- **Microsoft Power BI Desktop** (Latest version)
  - Download from: [PowerBI Desktop Official Page](https://powerbi.microsoft.com/desktop/)
  - Free license available
- **Microsoft Excel** (2016 or later)
  - Required for viewing and editing the data source
- **Git** (Optional, for cloning the repository)

## 🚀 Installation Steps

### Step 1: Install Power BI Desktop

1. Visit the [Microsoft Power BI Desktop download page](https://powerbi.microsoft.com/desktop/)
2. Click **Download free** button
3. Choose your preferred installation method:
   - **Microsoft Store** (Recommended)
   - **Direct download** (.msi installer)
4. Follow the installation wizard
5. Launch Power BI Desktop and sign in with your Microsoft account

### Step 2: Clone the Repository

**Option A: Using Git (Recommended)**
```bash
git clone https://github.com/krishn1122/blinkit-dashboard-PowerBI.git
cd blinkit-dashboard-PowerBI
```

**Option B: Download ZIP**
1. Go to the [repository page](https://github.com/krishn1122/blinkit-dashboard-PowerBI)
2. Click **Code** → **Download ZIP**
3. Extract the ZIP file to your preferred location

### Step 3: Open the Dashboard

1. **Launch Power BI Desktop**
2. **Open the dashboard file**:
   - Navigate to the project folder
   - Open `dashboard/Blinkit Sales Dashboard.pbix`
3. **Data source connection**:
   - Power BI will automatically detect the data source
   - The Excel file is located at `data/BlinkIT Grocery Data.xlsx`
   - If prompted, click **Load** to import the data

## 🔧 Configuration

### Data Source Setup

1. **Verify Data Connection**:
   - Go to **Home** → **Transform Data** → **Data Source Settings**
   - Ensure the path points to `data/BlinkIT Grocery Data.xlsx`
   - Update the path if necessary

2. **Refresh Data** (if needed):
   - Click **Home** → **Refresh**
   - This will reload the latest data from the Excel file

### Performance Optimization

1. **Enable Performance Analyzer**:
   - Go to **View** → **Performance Analyzer**
   - Use this to monitor dashboard loading times

2. **Optimize Visuals**:
   - Reduce the number of visible visuals per page
   - Use filters to limit data scope when needed

## 🛠️ Troubleshooting

### Common Issues and Solutions

#### Issue 1: Dashboard Won't Open
**Symptoms**: Error message when opening .pbix file
**Solutions**:
- Ensure you have the latest version of Power BI Desktop
- Check if the file is corrupted by downloading a fresh copy
- Verify you have proper permissions to access the file

#### Issue 2: Data Source Not Found
**Symptoms**: "Data source not found" error
**Solutions**:
```
1. Go to Home → Transform Data → Data Source Settings
2. Click "Change Source" 
3. Navigate to the correct path: data/BlinkIT Grocery Data.xlsx
4. Click OK and Apply Changes
```

#### Issue 3: Slow Performance
**Symptoms**: Dashboard loads slowly or becomes unresponsive
**Solutions**:
- Close other applications to free up memory
- Reduce the date range in filters
- Check if your system meets minimum requirements

#### Issue 4: Visuals Not Displaying Correctly
**Symptoms**: Charts appear blank or with error messages
**Solutions**:
- Check data source connection
- Verify data types in the Excel file
- Refresh the data (Home → Refresh)

## 📊 Data Requirements

### Excel Data Format
The `BlinkIT Grocery Data.xlsx` file should contain the following structure:

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| Date | Date | Transaction date |
| Item_Type | Text | Product category |
| Sales | Number | Sales amount |
| Rating | Number | Customer rating (1-5) |
| Outlet | Text | Store location |

### Data Validation
Before using custom data:
1. Ensure all required columns are present
2. Check for missing values
3. Verify data types match the expected format
4. Remove any duplicate entries

## 🔄 Updating the Dashboard

### Regular Maintenance
1. **Weekly**: Refresh data to get latest insights
2. **Monthly**: Review and update filters or calculations
3. **Quarterly**: Check for Power BI Desktop updates

### Adding New Data
1. Update the Excel file with new data
2. Open Power BI Desktop
3. Click **Home** → **Refresh**
4. Save the dashboard

## 📱 Sharing the Dashboard

### Power BI Service (Online)
1. Sign up for Power BI Service (free tier available)
2. Publish dashboard: **Home** → **Publish**
3. Share with team members via email

### Export Options
- **PDF**: File → Export → Export as PDF
- **PowerPoint**: File → Export → Export as PowerPoint
- **Image**: Right-click on visual → Export data

## 🆘 Support

If you encounter issues not covered in this guide:

1. **Check Documentation**: Review other files in the `documentation/` folder
2. **GitHub Issues**: Report bugs at the [repository issues page](https://github.com/krishn1122/blinkit-dashboard-PowerBI/issues)
3. **Power BI Community**: Visit [Power BI Community Forum](https://community.powerbi.com/)

## 📚 Additional Resources

- **Power BI Learning Path**: [Microsoft Learn - Power BI](https://docs.microsoft.com/learn/powerplatform/power-bi/)
- **DAX Functions**: [DAX Function Reference](https://docs.microsoft.com/dax/)
- **Best Practices**: [Power BI Best Practices](https://docs.microsoft.com/power-bi/guidance/)

---

**Next Steps**: After setup, review the [User Guide](USER_GUIDE.md) for detailed usage instructions.