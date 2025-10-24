# 📖 Portfolio Ladder Out - User Guide

Welcome to the Portfolio Ladder Out tool! This comprehensive guide will help you track your crypto portfolio, manage debt, analyze risk, and create strategic exit plans.

**Live App:** https://kevin-ladder-out.web.app

---

## 📑 Table of Contents

1. [Getting Started](#getting-started)
2. [Managing Your Portfolio](#managing-your-portfolio)
3. [Understanding the Dashboard](#understanding-the-dashboard)
4. [Risk Analysis](#risk-analysis)
5. [Creating Ladder Strategies](#creating-ladder-strategies)
6. [Data Management](#data-management)
7. [Tips & Best Practices](#tips--best-practices)

---

## 🚀 Getting Started

### First Time Setup

1. **Open the App**: Navigate to https://kevin-ladder-out.web.app
2. **Default Portfolio**: The app loads with sample data to help you understand the interface
3. **Clear Sample Data**: Delete the sample assets and add your own holdings

### Key Concepts

- **Asset Value**: Quantity × Current Price
- **Debt**: Money borrowed against an asset (e.g., using it as collateral)
- **Net Value**: Asset Value - Debt (your actual equity)
- **Leverage Ratio**: How much you're borrowing relative to your net worth
- **Ladder Strategy**: A planned exit strategy where you sell portions of an asset at increasing price targets

---

## 💼 Managing Your Portfolio

### Adding a New Asset

1. Click the **"➕ Add Asset"** button below the portfolio table
2. A new row appears with default values
3. Edit each field:
   - **Asset**: Ticker symbol (e.g., BTC, ETH, SOL)
   - **Quantity**: Amount you own
   - **Price**: Current price per unit in USD
   - **Debt**: Amount borrowed against this asset (leave as 0 if none)
   - **Location**: Select where the asset is stored

### Editing Asset Details

**Simply click on any input field and type:**
- Asset names are text fields
- Quantity, Price, and Debt are number fields
- Location is a dropdown menu

**Real-time Updates:**
- Asset Value, Net Value, and Percentage automatically recalculate
- Summary stats update instantly
- All calculations happen as you type!

### Removing Assets

1. Click the **"Remove"** button next to any asset
2. Confirm the deletion when prompted
3. The asset is removed and all calculations update

### Storage Locations

Track where your assets are stored:
- **Rabby**: Browser wallet
- **Backpack**: Backpack wallet
- **Slush**: Slush wallet
- **Coinbase**: Coinbase exchange
- **Cold Storage**: Hardware wallet or offline storage

---

## 📊 Understanding the Dashboard

### Portfolio Holdings Section

The main table displays:

| Column | Description |
|--------|-------------|
| **Asset** | Ticker and optional type (e.g., "Moonwell Lend/Borrow") |
| **Quantity** | Amount owned |
| **Price ($)** | Current price per unit |
| **Asset Value ($)** | Calculated: Quantity × Price (green background) |
| **Debt ($)** | Borrowed amount (red background) |
| **Net Value ($)** | Calculated: Asset Value - Debt (blue background) |
| **Net %** | Percentage of total portfolio |
| **Location** | Where the asset is stored |
| **Action** | Remove button |

### Summary Statistics

At the top of the page:

- **ASSETS**: Total value of all holdings (before debt)
- **DEBT**: Total amount owed
- **NET VALUE**: Your actual equity (Assets - Debt)

Below the portfolio table:

- **Total Assets**: Number of different assets held
- **Leverage Ratio**: Total Assets ÷ Net Value (shows how leveraged you are)
- **Largest Position**: Your biggest holding by net value
- **Cash/Stable Position**: Total USDC, USDT, and CASH holdings

---

## ⚠️ Risk Analysis

### Portfolio Health Status

The Risk Analysis section shows:

**When No Risks Detected (Green):**
- ✅ No significant risks
- Monitoring status for leverage, concentration, and lending positions
- Tips for tracking risk factors

**When Risks Are Present:**

1. **Leverage Risk** (Red/Orange/Green)
   - **Low** (<1.5x): Healthy leverage
   - **Medium** (1.5x-2x): Moderate risk, monitor closely
   - **High** (>2x): Dangerous levels, consider deleveraging
   - Shows current leverage ratio and total debt

2. **Concentration Risk** (Orange)
   - Flags any single asset exceeding 25% of your portfolio
   - Lists all concentrated positions with percentages
   - Suggests rebalancing to reduce risk

3. **Lending Positions** (Blue)
   - Shows assets with active debt
   - Displays Loan-to-Value (LTV) ratios
   - Warns about liquidation risks during volatility

---

## 🎯 Creating Ladder Strategies

### Strategy Dashboard

**To Open:**
1. Click the **"🎯 Generate Ladder Strategy"** button
2. A full-screen modal appears with your personalized strategy

**Dashboard Sections:**

#### 1. Metrics Cards
- **Total Ladder Value**: Combined value of all significant positions
- **Priority Assets**: Number of assets recommended for laddering
- **Assets with Debt**: Count of leveraged positions (red if >0)
- **Concentrated Positions**: Count of assets >25% of portfolio (orange if >0)

#### 2. Portfolio Visualization

**Composition Chart (Doughnut):**
- Shows your top 5 positions by value
- Percentage breakdown
- Hover for detailed values

**Priority Rankings (Bar Chart):**
- Assets ranked by priority score
- Color-coded:
  - **Red**: High priority (has debt)
  - **Orange**: Medium priority (concentrated)
  - **Blue**: Normal priority

#### 3. Priority Assets List

Each asset card shows:
- Asset name and size
- Net value and portfolio percentage
- Reasons for priority (debt, concentration)
- **"Calculate Ladder"** button

**Using "Calculate Ladder":**
1. Click the button on any asset
2. Dashboard closes automatically
3. Custom Ladder Calculator opens with that asset selected
4. Scroll to see the pre-calculated ladder strategy

#### 4. Strategy Recommendations

Dynamic recommendations based on your portfolio:

- **🚨 Deleverage Priority**: If you have debt
- **⚖️ Rebalancing Recommended**: If positions are concentrated
- **🎯 Ladder Strategy Tips**: General exit strategy guidance
- **🌙 Moon Bag Strategy**: Keep 15-20% for long-term holds
- **✅ Strong Position**: Appears when you have no leverage

**To Close Dashboard:**
- Click the **×** button in the top-right
- Click outside the modal (on the dark background)
- Press the ESC key

### Custom Ladder Calculator

**Location:** Below the portfolio table

**How to Use:**

1. **Select Asset**: Choose from the dropdown (excludes CASH and USDC)

2. **Set First Multiple**:
   - Starting price target (e.g., 1.5x = 50% gain)
   - Default: 1.5x

3. **Set Max Multiple**:
   - Highest price target (e.g., 5x = 400% gain)
   - Default: 5x

4. **Click "Calculate"**

**Understanding the Results:**

The calculator creates 5 ladder steps between your first and max multiple:

```
Step 1: 1.5x - Sell 10%
Step 2: 2.4x - Sell 15%
Step 3: 3.2x - Sell 15%
Step 4: 4.1x - Sell 20%
Step 5: 5.0x - Sell 20%
Remaining: 20% (Moon Bag)
```

For each step, you see:
- **Multiple**: Price target (e.g., 2.4x current price)
- **Target Price**: Actual USD price at that multiple
- **Sell Percentage**: Portion to sell
- **Cash Out Amount**: USD you'll receive (accounts for debt)

**Summary Box:**
- **Total Cash Out**: Sum of all ladder steps
- **Remaining Position**: Your "moon bag" percentage
- **Debt Reminder**: If applicable, shows debt to pay off

### Ladder Strategy Example

**Current Position:**
- Asset: BTC
- Quantity: 1 BTC
- Current Price: $50,000
- Net Value: $50,000
- Debt: $0

**Ladder Settings:**
- First Multiple: 1.5x
- Max Multiple: 5x

**Results:**
```
Step 1: 1.5x ($75,000)  - Sell 10% → Cash out $7,500
Step 2: 2.4x ($120,000) - Sell 15% → Cash out $18,000
Step 3: 3.2x ($160,000) - Sell 15% → Cash out $24,000
Step 4: 4.1x ($205,000) - Sell 20% → Cash out $41,000
Step 5: 5.0x ($250,000) - Sell 20% → Cash out $50,000

Total Cash Out: $140,500
Remaining: 20% (0.2 BTC) for long-term hold
```

---

## 💾 Data Management

### Saving Your Portfolio

1. Click **"💾 Save Portfolio"** button
2. Data is saved to your browser's local storage
3. Confirmation notification appears
4. Data persists even after closing the browser

**Important Notes:**
- Data is stored locally on your device only
- Not synced across devices
- Clearing browser data will delete your portfolio
- No login or account required

### Exporting Data

**To Export as CSV:**

1. Click **"📥 Export CSV"** button
2. File downloads automatically as `portfolio_YYYY-MM-DD.csv`
3. Open in Excel, Google Sheets, or any spreadsheet app

**CSV Contains:**
- All asset details
- Calculated values
- Debt information
- Location data
- Summary totals row

**Use Cases:**
- Backup your data
- Import to other tools
- Tax preparation
- Historical tracking
- Share with advisors

### Data Privacy

- **100% Local**: All data stays in your browser
- **No Server**: Nothing is uploaded or transmitted
- **No Tracking**: No analytics or data collection
- **No Account**: No login or registration needed
- **Your Control**: Clear browser data anytime to reset

---

## 💡 Tips & Best Practices

### Portfolio Management

1. **Update Prices Regularly**: Keep prices current for accurate calculations
2. **Track All Debt**: Include all borrowed amounts for accurate leverage tracking
3. **Use Descriptive Types**: Add type descriptions (e.g., "Aave Lend/Borrow") for clarity
4. **Organize by Location**: Track where assets are for security awareness
5. **Save Frequently**: Click Save Portfolio after making changes

### Risk Management

1. **Monitor Leverage**: Keep leverage ratio under 2x for safety
2. **Avoid Concentration**: No single position should exceed 25-30% of portfolio
3. **Track LTV Ratios**: For lending positions, keep LTV under 50% to avoid liquidation
4. **Review Regularly**: Check Risk Analysis section at least weekly
5. **Plan for Volatility**: Have deleveraging plans ready for market downturns

### Ladder Strategy Best Practices

1. **Start Conservative**: Use 1.5x-2x for first exits
2. **Scale Out Gradually**: Don't sell everything at once
3. **Keep Moon Bags**: Hold 15-20% for potential 10x+ gains
4. **Adjust for Debt**: Prioritize deleveraging in your ladder plan
5. **Account for Taxes**: Remember to set aside funds for capital gains taxes
6. **Update Regularly**: Recalculate ladders as prices change
7. **Write It Down**: Export or screenshot your ladder plan to track execution

### Debt Management

1. **Pay Off High-Risk First**: Focus on positions close to liquidation
2. **Reduce in Bull Runs**: Take profits to pay down leverage
3. **Calculate Interest**: Factor in borrowing costs
4. **Emergency Plans**: Know your liquidation prices
5. **Buffer Zones**: Keep LTV well below liquidation thresholds

### Using the Strategy Dashboard

1. **Check Before Bull Runs**: Generate strategy before major price moves
2. **Follow Priorities**: Act on red (high priority) items first
3. **One-Click Setup**: Use "Calculate Ladder" buttons for quick planning
4. **Review Recommendations**: Read all strategy cards carefully
5. **Adjust to Goals**: Modify suggestions based on your risk tolerance

### Data Backup

1. **Export Monthly**: Download CSV backups regularly
2. **Multiple Devices**: Take screenshots or export from each device you use
3. **Version Control**: Keep dated copies of exports
4. **Test Restore**: Practice clearing and re-entering data
5. **Cloud Backup**: Store CSV exports in Google Drive or Dropbox

---

## 🛟 Troubleshooting

### Portfolio Not Saving

**Issue**: Changes disappear after refresh

**Solutions:**
1. Click "💾 Save Portfolio" button explicitly
2. Check if browser is in private/incognito mode (doesn't save data)
3. Verify browser allows localStorage (check privacy settings)
4. Try a different browser
5. Export CSV as backup

### Calculations Seem Wrong

**Issue**: Numbers don't add up

**Checks:**
1. Verify all quantities are correct
2. Check prices are accurate and current
3. Ensure debt amounts are entered correctly
4. Refresh the page to recalculate
5. For percentages, remember they're based on net value (after debt)

### Can't Edit Fields

**Issue**: Input fields not responding

**Solutions:**
1. Refresh the page
2. Clear browser cache
3. Try a different browser
4. Check if JavaScript is enabled
5. Disable browser extensions that might interfere

### Dashboard Not Opening

**Issue**: Strategy Dashboard button doesn't work

**Solutions:**
1. Refresh the page
2. Check browser console for errors (F12)
3. Verify browser supports modern JavaScript
4. Try a different browser
5. Clear browser cache and reload

### Charts Not Displaying

**Issue**: Visualizations don't appear in Strategy Dashboard

**Solutions:**
1. Check internet connection (Chart.js loads from CDN)
2. Verify browser supports Canvas API
3. Disable ad blockers temporarily
4. Refresh the page
5. Try a different browser

---

## 🔐 Security & Privacy

### What's Stored Locally

- Portfolio asset data
- Quantities and prices
- Debt amounts
- Location information

### What's NOT Stored

- No personal information
- No login credentials
- No API keys
- No transaction history
- No wallet addresses

### Security Best Practices

1. **Don't Share Screenshots**: Avoid sharing portfolio screenshots publicly
2. **Use Private Browsing**: For sensitive portfolio reviews
3. **Lock Your Device**: Protect access to your computer/phone
4. **Clear Data**: When using shared computers, clear browser data after use
5. **Backup Offline**: Store CSV exports in encrypted folders

---

## 📞 Support & Feedback

### Getting Help

- **GitHub Issues**: https://github.com/defiuniversity-xyz/portfolio-tracker/issues
- **Documentation**: Check CLAUDE.md and README.md in the repository

### Reporting Bugs

When reporting issues, include:
1. Browser and version
2. Steps to reproduce
3. Expected vs actual behavior
4. Screenshots if applicable
5. Any error messages from browser console

### Feature Requests

We welcome suggestions! Open an issue on GitHub with:
1. Clear description of the feature
2. Use case / problem it solves
3. How you'd like it to work
4. Any examples from other tools

---

## 📚 Additional Resources

### Understanding Leverage

- **1.0x**: No leverage, 100% equity
- **1.5x**: Moderate leverage, 67% equity
- **2.0x**: High leverage, 50% equity
- **3.0x**: Very high risk, 33% equity
- **4.0x+**: Extreme risk, <25% equity

### Recommended LTV Ranges

- **Stablecoins**: 75-85% safe
- **Major Cryptos (BTC/ETH)**: 40-50% safe
- **Altcoins**: 25-35% maximum
- **Volatile Assets**: 20% or less

### Exit Strategy Framework

1. **Take Initial** (1.5-2x): Recover initial investment
2. **Take Profits** (2-4x): Realize gains, reduce position
3. **Moon Bag** (20%): Hold for potential 10-20x
4. **Never Sell All**: Keep exposure to upside
5. **Ladder Gradually**: Don't try to time tops

---

## ⚖️ Disclaimer

**This tool is for informational and planning purposes only.**

- Not financial advice
- Do your own research
- Verify all calculations independently
- Consult with qualified financial advisors
- Past performance doesn't guarantee future results
- Cryptocurrency investments carry significant risk
- You are responsible for your own financial decisions

---

## 🎓 Quick Reference

### Keyboard Shortcuts

- **ESC**: Close Strategy Dashboard modal
- **Tab**: Navigate between input fields
- **Enter**: Submit forms (Save, Calculate)

### Color Coding

- **Green**: Calculated asset values (positive)
- **Red**: Debt amounts (liabilities)
- **Blue**: Net values (equity)
- **Gray**: Editable input fields
- **Orange**: Medium priority warnings
- **Red borders**: High priority warnings

### Common Calculations

```
Asset Value = Quantity × Price
Net Value = Asset Value - Debt
Leverage Ratio = Total Asset Value ÷ Total Net Value
Position % = (Asset Net Value ÷ Total Net Value) × 100
LTV = (Debt ÷ Asset Value) × 100
```

---

## 🚀 Getting the Most Out of Portfolio Ladder Out

1. **Set Up Once**: Enter all your positions completely
2. **Update Daily**: Keep prices current during active trading
3. **Review Weekly**: Check Risk Analysis for warnings
4. **Plan Monthly**: Generate Strategy Dashboard and adjust ladders
5. **Execute Discipline**: Follow your ladder plans when targets hit
6. **Track Results**: Export CSV monthly to track performance over time

---

**Built with ❤️ for the crypto community**

*Last Updated: 2025*
