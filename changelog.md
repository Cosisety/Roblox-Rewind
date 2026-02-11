# Changelog

All notable changes to Roblox Rewind will be documented in this file.

---

## [0.3.4] - 2026-02-06

### Added
- **More Real-World Comparisons**: More variety in spending comparisons — items are now randomized each visit instead of showing the same three every time
- **Comparison Price Labels**: Each comparison item now shows its unit price (e.g. "at $5.50 each") for context, fully translated in all 10 languages
- **Zero-Purchase Handling**: Accounts with no spending history now show a friendly message instead of empty sections, with different messages based on account age
- **Anonymous Usage Data**: Optional anonymous telemetry to help improve the extension — tracks basic events like load success and fetch duration, with no personal data collected. Opt out anytime from the privacy modal
- **Smart Retry**: When data is incomplete due to rate limits, a "Retry incomplete" button now appears that only re-fetches the failed transaction types instead of starting over from scratch
- **New Locale Scaffolds**: Added Italian (it), Russian (ru), Turkish (tr), and Vietnamese (vi) locale files (English fallback ready for translation)

### Changed
- **Comparison Wording**: Updated comparison intro text to work better with all comparison types (updated across all 10 languages)
- **Translated Loading Messages**: Progress text during data fetching is now fully translated in all 10 languages
- **Empty Section Cleanup**: Sections with no data (charts, leaderboards, breakdowns) now hide automatically instead of showing placeholder text
- **Privacy Disclosure Updated**: Privacy modal now includes details about anonymous usage data and an opt-out toggle
- **Privacy Policy Link**: Privacy modal now links directly to the PrivacyPolicy.md file
- **Landing Scale**: Initial screen typography, buttons, and spacing are slightly larger while on the home screen
- **Cache Copy**: Footer + caching description now say "automatically cached" and reflect the user's selected cache duration
- **Welcome Copy**: Initial heading now reads "Welcome to Roblox Rewind!"

### Fixed
- **Share Image Text Overflow**: Long item names no longer overflow outside their cards in the share image
- **Privacy Text Accuracy**: Updated privacy modal to clarify that Roblox data stays local while anonymous usage stats are sent
- **Footer Version**: Footer now correctly shows the current version
- **Completeness Banner Cleanup**: The incomplete data banner now clears after a successful retry
- **Retry Toast Localization**: "All data is already complete" now uses i18n
- **Telemetry Toggle Alignment**: Toggle is now centered properly in the privacy modal

### Security
- **Removed Web Accessible Resources**: Extension resources are no longer web-accessible since no external pages need them — tighter security surface

---

## [0.3.3] - 2026-02-06

### Changed
- **CSS Design Token System**: All colors, borders, and radii are now CSS custom properties in `:root`, making theme changes a single-variable edit
- **CSS Extracted to Separate File**: Moved ~1,200 lines of inline CSS from `dashboard.html` into `dashboard.css` for better maintainability and IDE tooling
- **Share Image Resolution Doubled**: Canvas base width increased from 600px to 1200px for sharp rendering on social media (Twitter, Discord, Instagram)
- **Improved Color Contrast**: Secondary text color bumped from `#707070` to `#9a9a9a` (~5:1 contrast ratio), meeting WCAG AA accessibility standards

### Added
- **Avatar Placeholder**: Share image now shows the user's initial in a styled circle when the avatar image fails to load, instead of skipping the avatar entirely
- **Analysis Memoization**: `analyzeSpending()` results are now cached by data reference, eliminating redundant computation when opening the share modal, switching themes, or changing years

### Fixed
- **Share Image Top Purchase Truncation**: Name truncation increased from 25 to 40 characters to use the larger canvas space

---

## [0.3.2] - 2026-02-04

### Added
- **Data Completeness Warning**: Shows a dismissible banner when transaction data may be incomplete due to rate limits or errors

### Changed
- **Faster Data Fetching**: Transaction types are now fetched in parallel, significantly reducing load times
- **Cache Duration Behavior**: Shortening the cache duration now immediately clears stale cached data instead of waiting for next refresh
- **Category Labels**: Friendlier names in the spending breakdown chart (e.g. "System Purchases" instead of "RobloxProduct")

### Security
- **Restricted Web Accessible Resources**: Extension resources no longer accessible from arbitrary websites (restricted to roblox.com)
- **Message Sender Validation**: Background service worker now validates message origin before processing

### Fixed
- **API Robustness**: Better handling of edge cases like duplicate cursors and rate limit tracking
- **Global Rate Limit Coordination**: When one request hits a 429, all parallel workers now pause together instead of continuing to fire
- **Progress Bar Stability**: Loading bar no longer jumps backward when parallel workers complete out of order

---

## [0.3.1] - 2026-02-02

### Added
- **Cache Duration Setting**: Users can now choose how long to keep transaction data cached (1 hour, 6 hours, 24 hours, or 1 week) via Advanced Features → Cache Duration
- **New Languages**: Added French (fr), German (de), Indonesian (id), and Hindi (hi) support
- **Completed Translations**: All existing languages (es, ko, pt, ja, zh) now have 100% translation coverage

### Changed
- **Privacy Improvement**: Added `noreferrer` to external links for better privacy
- **Privacy Disclosure**: Privacy modal now explicitly mentions local caching of transaction data

---

## [0.3.0] - 2026-02-02

### Changed
- **Theme Overhaul**: Replaced purple/blue theme with Roblox's official dark mode colors
  - Background: Solid dark `#111217` (was gradient)
  - Accent: Roblox blue `#2bb1ff` (was purple `#667eea`)
  - Updated all UI elements: cards, buttons, modals, toasts, charts, scrollbars
  - Share image themes remain unchanged for variety
- **New Logo**: Updated extension icons

### Fixed
- **Code Quality**: Added radix parameter to `parseInt()` calls for safer number parsing
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
