# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page HTML application for cryptocurrency portfolio tracking with integrated debt management and ladder strategy calculation. The application runs entirely in the browser with no backend dependencies.

**Main File**: `claude source.txt` - Contains the complete HTML/CSS/JavaScript application

## Architecture

### Data Model
The portfolio is stored as a JavaScript array of asset objects with the following structure:
```javascript
{
  asset: string,      // Asset ticker (e.g., 'cbBTC', 'wETH')
  type: string,       // Optional type description (e.g., 'Moonwell Lend/Borrow')
  quantity: number,   // Amount held
  price: number,      // Current price per unit
  debt: number,       // Outstanding debt against this asset
  location: string    // Storage location (Rabby, Backpack, Slush, Coinbase, Cold Storage)
}
```

### State Management
- **Persistence**: Portfolio data is persisted to `localStorage` under the key `portfolioDataV2`
- **Initialization**: On load, the app checks for saved data and falls back to default portfolio if none exists
- **Updates**: The `renderPortfolio()` function re-renders the entire table and triggers `updateSummary()` for calculations

### Key Calculations
1. **Asset Value** = quantity × price
2. **Net Value** = Asset Value - debt
3. **Total Net Value** = Sum of all net values
4. **Leverage Ratio** = Total Asset Value ÷ Total Net Value
5. **Net Percentage** = (Asset Net Value ÷ Total Net Value) × 100

### Core Functions

**Data Operations:**
- `loadFromLocal()` - Loads portfolio from localStorage on initialization
- `saveToLocal()` - Persists portfolio to localStorage
- `updateAsset(index, field, value)` - Updates a specific field and triggers re-render
- `addNewAsset()` - Adds new asset with default values
- `removeAsset(index)` - Removes asset after confirmation

**UI & Display:**
- `renderPortfolio()` - Renders the entire portfolio table with inline editing
- `updateSummary()` - Calculates and updates all summary statistics
- `showNotification(message, type)` - Displays temporary success/error notifications

**Analysis & Strategy:**
- `calculateCustomLadder()` - Generates ladder strategy for selected asset
- `analyzeRisk(netTotal, totalDebt, totalValue)` - Displays leverage and concentration risks
- `generateLadderStrategy()` - Summarizes top positions for ladder strategies
- `exportCSV()` - Exports portfolio data to CSV file

## Development Notes

### Editing the Application
When making changes to the application:
1. All code is in a single HTML file (`claude source.txt`)
2. The file contains three sections: HTML structure (lines 1-411), embedded CSS (lines 8-310), and JavaScript (lines 412-845)
3. CSS uses a gradient blue theme with card-based layout
4. JavaScript uses vanilla JS with no framework dependencies

### Data Structure Migrations
The app includes backward compatibility for data migrations:
- localStorage key changed from `portfolioData` to `portfolioDataV2` when debt field was added
- When loading saved data, the app ensures all assets have a `debt` field (defaults to 0)

### UI Color Coding
- **Green backgrounds** (`#e8f5e9`) - Calculated asset values
- **Red backgrounds** (`#ffebee`) - Debt input fields
- **Blue backgrounds** (`#e3f2fd`) - Net value cells
- **Gray backgrounds** (`#f8f9fa`) - Editable input fields

### Risk Analysis Thresholds
- **Leverage Risk**: Low (<1.5x), Medium (1.5x-2x), High (>2x)
- **Concentration Risk**: Flagged when single asset exceeds 25% of net portfolio
- **LTV Monitoring**: Displayed for assets with lending/borrowing positions

## Testing Changes

Since this is a standalone HTML application:
1. Open `claude source.txt` in a web browser
2. Test data persistence by:
   - Making changes
   - Clicking "Save Portfolio"
   - Refreshing the page
   - Verifying changes persisted
3. Test calculations by entering various quantities, prices, and debt amounts
4. Test CSV export functionality
5. Test ladder calculator with different assets and multiplier ranges

## Common Modifications

**Adding new location options:**
Edit the select element in `renderPortfolio()` around line 518-525

**Changing ladder calculation logic:**
Modify `calculateCustomLadder()` function (lines 621-682)

**Adjusting risk thresholds:**
Update conditions in `analyzeRisk()` function (lines 684-769)

**Modifying default portfolio:**
Edit the `portfolio` array initialization (lines 414-427)
