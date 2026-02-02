# Changelog

All notable changes to Roblox Rewind will be documented in this file.

---

## [0.3.0] - 2026-02-02

### Changed
- **Theme Overhaul**: Replaced purple/blue theme with Roblox's official dark mode colors
  - Background: Solid dark `#111217` (was gradient)
  - Accent: Roblox blue `#2bb1ff` (was purple `#667eea`)
  - Updated all UI elements: cards, buttons, modals, toasts, charts, scrollbars
  - Share image themes remain unchanged for variety

### Fixed
- **Comparison Text Clarity**: "Your Roblox Identity" section now clearly shows alternatives
  - Changed intro to "That's enough to buy any one of these:"
  - Added "or" separators between comparison items
  - Values now round up to at least 1 (no more "0.7 of a car")
- **Progress Bar Stability**: Loading bar no longer jumps backward during rate limits
  - Tracks highest achieved progress and slowly creeps forward
  - Provides smoother, more stable loading experience

### Added
- **Load Time Warning**: Initial screen now displays warning that first load may take up to 3 minutes
- This changelog file

---

## [0.2.0] - 2026-01

### Added
- **Player Classifications**: Window Shopper, Casual Spender, Dedicated Player, Big Spender, Robux Enthusiast, Certified Whale
- **Real-world Comparisons**: Shows what you could've bought (Big Macs, Netflix months, etc.)
- **Currency Localization**: Detects user's locale, converts USD to local currency
- **Share Image Feature**: 4 themes (Cosmic, Roblox, Minimal, Spotify) with high-DPI rendering
- **Toast Notification System**: Replaced alert() dialogs
- **Internationalization (i18n)**: Support for 6 languages (en, es, ko, pt, ja, zh)
- **Dev Test Mode**: Random data generator for testing (when dev-config.json exists)

### Changed
- Improved color contrast for accessibility
- Added keyboard navigation for dropdown menus
- Added ARIA accessibility labels
- Mobile-responsive modal styles

### Fixed
- Rate limiting UX: Shows friendly messages instead of technical errors

---

## [0.1.0] - 2026-01

### Added
- Initial release on Chrome Web Store
- Transaction history fetching from Roblox API
- Spending analysis with USD estimates
- Membership detection (BC era and Premium era)
- Yearly and category spending charts
- Purchase breakdown by source (Creator vs Roblox)
- Membership timeline visualization
- Fun Facts & Insights section
- Data caching (1 hour TTL)
- Export data feature
