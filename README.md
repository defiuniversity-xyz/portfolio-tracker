# 📊 Advanced Portfolio Tracker with Debt Management

A comprehensive cryptocurrency portfolio tracking application with integrated debt management, leverage analysis, and ladder strategy calculator. Built as a single-page application with no backend dependencies.

## 🌟 Features

### Core Portfolio Management
- **Real-time Portfolio Tracking**: Track multiple crypto assets across different platforms
- **Multi-location Support**: Organize assets by wallet (Rabby, Backpack, Slush, Coinbase, Cold Storage)
- **Live Calculations**: Automatic calculation of asset values, net positions, and percentages
- **Inline Editing**: Edit quantities, prices, and debt amounts directly in the table

### Debt & Leverage Management
- **Debt Tracking**: Track borrowed amounts against each asset
- **Net Value Calculation**: Automatically calculate net positions (Asset Value - Debt)
- **Leverage Ratio**: Real-time leverage ratio calculation and monitoring
- **Risk Analysis**:
  - Leverage risk assessment (Low/Medium/High)
  - Concentration risk alerts (positions >25%)
  - LTV monitoring for lending positions

### Ladder Strategy Calculator
- **Custom Ladder Generation**: Create custom exit strategies for any asset
- **Configurable Multipliers**: Set your own price targets (e.g., 1.5x to 5x)
- **Smart Distribution**: Automatically calculates sell percentages at each level
- **Debt-Aware**: Takes outstanding debt into account for accurate cash-out calculations
- **Moon Bag Planning**: Reserves portion for long-term holding

### Data Management
- **Local Persistence**: All data stored in browser localStorage
- **CSV Export**: Export your entire portfolio to CSV for external analysis
- **Auto-save**: Quick save functionality to persist changes
- **Data Privacy**: No server-side storage - your data never leaves your browser

## 🚀 Getting Started

### Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/<your-username>/portfolio-tracker.git
   cd portfolio-tracker
   ```

2. **Open in browser**:
   Simply open `index.html` in your web browser:
   ```bash
   # macOS
   open index.html

   # Linux
   xdg-open index.html

   # Windows
   start index.html
   ```

3. **Or use a local server** (recommended):
   ```bash
   # Python 3
   python -m http.server 8000

   # Node.js (if you have http-server installed)
   npx http-server

   # Firebase (if configured)
   firebase serve
   ```

   Then navigate to `http://localhost:8000` (or respective port)

### Deployment

#### Deploy to Firebase Hosting

1. **Install Firebase CLI**:
   ```bash
   npm install -g firebase-tools
   ```

2. **Login to Firebase**:
   ```bash
   firebase login
   ```

3. **Initialize Firebase** (first time only):
   ```bash
   firebase init hosting
   ```
   - Select your Firebase project or create a new one
   - Set public directory to `.` (current directory)
   - Configure as single-page app: Yes
   - Don't overwrite index.html

4. **Deploy**:
   ```bash
   firebase deploy
   ```

5. **Access your app**:
   Your app will be available at `https://<project-id>.web.app`

## 📖 Usage Guide

### Adding Assets

1. Click the "➕ Add Asset" button
2. Edit the asset name, quantity, and price
3. Optionally add debt amount if borrowed against
4. Select the storage location from the dropdown
5. Click "💾 Save Portfolio" to persist changes

### Tracking Debt

- Enter debt amounts in the "Debt ($)" column for any assets with borrowed funds
- Net Value automatically calculates as: Asset Value - Debt
- Monitor your leverage ratio in the summary section
- Risk analysis will flag high leverage positions

### Creating Ladder Strategies

1. Navigate to the "Custom Ladder Calculator" section
2. Select an asset from the dropdown
3. Set your first multiple (e.g., 1.5x current price)
4. Set your maximum multiple (e.g., 5x current price)
5. Click "Calculate" to generate the ladder
6. Review the suggested sell percentages at each price level

### Exporting Data

- Click "📥 Export CSV" to download your portfolio as a CSV file
- File includes all asset details, values, and debt information
- Filename format: `portfolio_YYYY-MM-DD.csv`

### Risk Analysis

The app automatically analyzes your portfolio for:
- **Leverage Risk**: Warns if leverage exceeds safe thresholds (>1.5x)
- **Concentration Risk**: Flags positions that represent >25% of portfolio
- **Lending Positions**: Monitors LTV ratios for assets with active loans

## 🏗️ Architecture

### Technology Stack
- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Charts**: Chart.js 4.4.0 (CDN)
- **Storage**: Browser localStorage
- **Hosting**: Firebase Hosting (Google Cloud Platform)

### Data Structure
```javascript
{
  asset: string,      // Asset ticker (e.g., 'BTC', 'ETH')
  type: string,       // Optional type (e.g., 'Moonwell Lend/Borrow')
  quantity: number,   // Amount held
  price: number,      // Current price per unit
  debt: number,       // Outstanding debt against asset
  location: string    // Storage location
}
```

### Key Calculations
- **Asset Value** = quantity × price
- **Net Value** = Asset Value - debt
- **Leverage Ratio** = Total Asset Value ÷ Total Net Value
- **Position %** = (Asset Net Value ÷ Total Net Value) × 100

## 🔒 Privacy & Security

- **No Server Communication**: Application runs entirely in your browser
- **Local Storage Only**: Data persisted using browser localStorage
- **No Analytics**: No tracking or data collection
- **No Authentication**: No user accounts or passwords required
- **Your Data, Your Control**: Clear browser data to reset everything

## 🛠️ Development

### File Structure
```
portfolio-tracker/
├── index.html              # Main application file
├── CLAUDE.md              # AI assistant guidance
├── README.md              # This file
├── .gitignore             # Git ignore rules
├── firebase.json          # Firebase configuration
└── .firebaserc            # Firebase project settings
```

### Making Changes

1. Edit `index.html` with your preferred editor
2. Test changes by opening in browser or using local server
3. Commit changes:
   ```bash
   git add .
   git commit -m "Description of changes"
   git push origin main
   ```
4. Deploy updates:
   ```bash
   firebase deploy
   ```

### Code Organization

The `index.html` file contains three main sections:
- **HTML** (lines 1-411): Structure and layout
- **CSS** (lines 8-310): Styling with gradient theme
- **JavaScript** (lines 412-845): Application logic

See `CLAUDE.md` for detailed architecture documentation.

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes
4. Test thoroughly in your browser
5. Commit: `git commit -m "Add amazing feature"`
6. Push: `git push origin feature/amazing-feature`
7. Open a Pull Request

### Ideas for Contributions
- Add more chart visualizations
- Implement historical price tracking
- Add price API integrations
- Create mobile-responsive improvements
- Add export to other formats (JSON, Excel)
- Implement portfolio comparison features
- Add tax calculation helpers

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Built with vanilla JavaScript for maximum compatibility
- Charts powered by [Chart.js](https://www.chartjs.org/)
- Hosted on [Firebase Hosting](https://firebase.google.com/docs/hosting)

## 📞 Support

For issues, questions, or suggestions:
- Open an [Issue](https://github.com/<your-username>/portfolio-tracker/issues)
- Submit a [Pull Request](https://github.com/<your-username>/portfolio-tracker/pulls)

---

**Note**: This tool is for tracking purposes only. Always verify calculations independently and consult with financial advisors before making investment decisions.
