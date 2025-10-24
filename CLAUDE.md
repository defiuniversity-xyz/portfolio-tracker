# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page HTML application for cryptocurrency portfolio tracking with integrated debt management and ladder strategy calculation. The application runs entirely in the browser with no backend dependencies.

**Main File**: `index.html` - Contains the complete HTML/CSS/JavaScript application

## Development Commands

### Local Development
```bash
# Open directly in browser
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows

# Or serve locally (recommended)
python -m http.server 8000  # Python 3
npx http-server  # Node.js
firebase serve  # Firebase (port 5000)
```

### Deployment (Firebase Hosting)
```bash
# First time setup
firebase login
firebase init hosting  # Set public directory to ".", configure as SPA, don't overwrite index.html

# Test before deploying
firebase serve

# Deploy to production
firebase deploy
# or
firebase deploy --only hosting
```

### Testing
Since this is a client-side only application:
1. Open `index.html` in browser
2. Test data persistence: Make changes → Save Portfolio → Refresh → Verify persistence
3. Test calculations with various quantities, prices, and debt amounts
4. Test CSV export functionality
5. Test ladder calculator with different assets and multiplier ranges

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

### File Structure
All code is contained in `index.html`:
- **HTML Structure** (lines 1-411): Page layout, cards, tables, forms
- **Embedded CSS** (lines 8-310): Gradient blue theme with card-based layout
- **JavaScript Logic** (lines 412-845): Application state and functions

### Core Functions

**Data Operations:**
- `loadFromLocal()` - Loads portfolio from localStorage on initialization (index.html:430)
- `saveToLocal()` - Persists portfolio to localStorage (index.html:447)
- `updateAsset(index, field, value)` - Updates a specific field and triggers re-render
- `addNewAsset()` - Adds new asset with default values
- `removeAsset(index)` - Removes asset after confirmation

**UI & Display:**
- `renderPortfolio()` - Renders the entire portfolio table with inline editing (index.html:478)
- `updateSummary()` - Calculates and updates all summary statistics (index.html:559)
- `showNotification(message, type)` - Displays temporary success/error notifications (index.html:458)

**Analysis & Strategy:**
- `calculateCustomLadder()` - Generates ladder strategy for selected asset (index.html:622)
- `analyzeRisk(netTotal, totalDebt, totalValue)` - Displays leverage and concentration risks (index.html:685)
- `generateLadderStrategy()` - Summarizes top positions for ladder strategies (index.html:802)
- `exportCSV()` - Exports portfolio data to CSV file (index.html:772)

## Development Notes

### Technology Stack
- **Pure vanilla JavaScript** - No build process or dependencies required
- **Chart.js 4.4.0** - Loaded via CDN for visualizations
- **localStorage API** - Client-side persistence (key: `portfolioDataV2`)
- **No backend** - All logic runs in the browser

### Data Structure Migrations
The app includes backward compatibility:
- localStorage key changed from `portfolioData` to `portfolioDataV2` when debt field was added (index.html:431)
- On load, ensures all assets have a `debt` field (defaults to 0) for older saved data (index.html:436)

### UI Color Coding
- **Green backgrounds** (`#e8f5e9`) - Calculated asset values
- **Red backgrounds** (`#ffebee`) - Debt input fields
- **Blue backgrounds** (`#e3f2fd`) - Net value cells
- **Gray backgrounds** (`#f8f9fa`) - Editable input fields

### Risk Analysis Thresholds
- **Leverage Risk**: Low (<1.5x), Medium (1.5x-2x), High (>2x) - index.html:695
- **Concentration Risk**: Flagged when single asset exceeds 25% of net portfolio - index.html:720
- **LTV Monitoring**: Calculated for assets with lending/borrowing positions - index.html:755

### Ladder Strategy Logic
Default ladder configuration (index.html:638):
- **Steps**: 5 price levels
- **Distribution**: 10% at first level, 15% at levels 2-3, 20% at levels 4-5
- **Moon Bag**: Remaining percentage held long-term
- **Debt-Aware**: Takes outstanding debt into account when calculating cash-out values

## Common Modifications

**Adding new wallet location:**
Edit the select dropdown options in `renderPortfolio()` around index.html:518-525

**Changing ladder calculation steps/percentages:**
Modify the steps, increment, and sellPercent logic in `calculateCustomLadder()` (index.html:638-654)

**Adjusting risk analysis thresholds:**
Update leverage/concentration conditions in `analyzeRisk()` (index.html:695, index.html:720)

**Modifying default portfolio data:**
Edit the `portfolio` array initialization (index.html:414-427)

**Changing location options:**
Update the select element in renderPortfolio where location dropdown is defined (around index.html:520)

## Firebase Configuration

The project is configured for Firebase Hosting:
- **Public directory**: `.` (root directory)
- **SPA rewrites**: All routes point to `/index.html`
- **Cache control**: 1-hour cache for static assets
- **Ignored files**: `firebase.json`, `CLAUDE.md`, `README.md`, dotfiles, `node_modules`

See `DEPLOYMENT.md` for detailed deployment instructions.
