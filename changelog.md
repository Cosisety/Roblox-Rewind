# Changelog

All notable changes to Roblox Rewind will be documented in this file.

---

## [0.4.0] - 2026-03-15

### Added
- **Compare Mode**: Added a new compare section that supports **Year vs Year** and **Category vs Category** views with side-by-side metric deltas
- **Monthly Digest**: Added a rolling **Last 30 Days vs Prior 30 Days** digest with full drilldowns for top categories, items, and games
- **Compare Share Layout**: Added a new **Compare** share layout and support across all existing share themes

### Changed
- **Engagement Telemetry (Aggregate Only)**: Added aggregate interaction events for compare/digest usage and session timing signals without sending personal or transaction-content data
- **Settings Persistence**: Compare selections and digest expand/collapse state are now saved locally and restored across sessions
- **Trust Messaging in Insights**: Compare and digest views now show a clear "based on available data" label when source completeness is partial
- **Compare Access Flow**: Compare Mode is now opened from a dedicated top action button (next to Share Image and Advanced Features) instead of being embedded directly in the main results stream
- **Digest Placement**: Monthly Digest now lives inside the Compare experience for a cleaner main dashboard layout

### Quality
- **Cross-Platform Parity**: Updated Chrome and Firefox builds with matching compare/digest behavior and release-gate validation
- **Compare Share Output**: Improved compare share rendering so metric text scales and fits more cleanly, while keeping consistent preview sizing with other share layouts
- **Compare Year Selection in Share**: Specific-year selection now properly drives compare-share period pairing (selected year versus prior available year)

### Fixed
- **Membership History Refresh Accuracy**: Corrected membership-history rebuild caching so timeline details refresh when the underlying month data changes
- **Year Share Accuracy**: Corrected year-specific share stats to use the selected year's true top purchase and real-money semantics (cash spent, not value-spent)
- **Cache Safety + Recovery**: Added stricter cache-shape validation, normalized cache-duration values, and clearer cache-withheld/auth messaging when cached results cannot be safely shown
- **Refresh Race Guard**: Prevented stale auto-load renders from racing against manual refresh/retry flows
- **Download Reliability**: Added explicit download API failure handling for export/share actions instead of silent failures
- **Dashboard Reuse on Open**: Popup now focuses an existing dashboard tab when available instead of always opening duplicates

### Security
- **Firefox Abuse Controls (Cloud Features)**: Added additional request hardening for Firefox-origin telemetry/game-code traffic with lightweight rate limiting and stricter request-shape checks

### Performance
- **Faster First Paint of Results**: Avatar fetching for share output is now preloaded in the background so core dashboard stats/charts render sooner
- **Share Modal Efficiency**: Year selector options now avoid unnecessary rebuilds when source years are unchanged
- **Top Games Share Rendering**: Game icon image decoding for Top 5 share layout now starts in parallel to reduce wait time before cards draw

---

## [0.3.9] - 2026-03-01

### Added
- **Performance Mode Setting**: Added a new settings control with `Auto`, `On (Lower Effects)`, and `Off (Best Visuals)` modes to tune rendering cost on slower devices
- **Stage-Based Load Status**: Loading now reports clear stages (`login`, `cache`, `fetch`, `retry`, `analysis`, `render`) with ETA bands for better long-load clarity

### Changed
- **Reliability-First Timing Telemetry**: Added aggregate runtime timing segments for auth, cache, fetch, retry, analysis, and render to improve performance tuning without collecting personal data
- **Adaptive Low-End Rendering**: Auto mode now applies a conservative low-end profile on constrained devices while preserving all data/features
- **Canvas DPR Control**: Chart and share-image rendering now caps device pixel ratio in low-end mode to reduce GPU/memory pressure
- **Privacy Disclosure Refresh**: Updated privacy policy wording to reflect performance-mode settings storage and aggregate timing/profile diagnostics in optional telemetry

### Performance
- **Top Games Re-Render Guard**: Top Games list now skips rebuilds when metric, locale, and source rows are unchanged
- **Reduced Visual Cost Profile**: Low-end profile trims non-essential transitions and heavy shadows to improve interaction smoothness on weaker hardware

---

## [0.3.8] - 2026-03-01

### Security
- **Release Validation Guardrails**: Added stronger release validation guardrails to prevent incomplete public bundles and stripped-code regressions

### Changed
- **Cross-Platform Release Checks**: Release validation now enforces Chrome and Firefox parity checks before packaging
- **Build Hardening**: Public package structure, endpoint/platform separation, and manifest safety rules are now validated as blocking release gates

---

## [0.3.7] - 2026-02-28

### Added
- **Data Trust Panel**: Added a dedicated trust panel below summary metrics with clear run status, plain-language explanations, and optional details
- **Top Games Up Front**: Moved Top Games to a higher-priority position near the top of results for faster insight

### Changed
- **Top Games Interaction**: Top Games now supports stable metric ranking by either Robux or purchase count, with deterministic tie-break ordering
- **Top Games Navigation**: Clicking a Top Games row now opens that experience on Roblox in a new tab
- **Retry Clarity**: Retry messaging now uses clearer non-technical recovery language in both panel summaries and toasts
- **Section Consistency**: Tightened section spacing and heading rhythm for Trust, Top Games, charts, and related analytics blocks
- **Verified Data Placement**: Moved the verification panel to the bottom of results and retitled it as **Verified Data** with a compact checkmark style

### Fixed
- **Trust State Persistence**: Trust panel expand/collapse preference now persists across sessions
- **Coverage Localization**: Top Games coverage, metric values, and row metadata now use i18n-backed strings for runtime language switching
- **Keyboard Accessibility**: Top Games clickable rows are keyboard-accessible with improved screen-reader labels

---

## [0.3.6] - 2026-02-27

### Security
- **Cache Identity Enforcement**: Cached results are now shown only when they match the currently authenticated Roblox account ID
- **Timestamp Validation Hardening**: Analysis paths now skip malformed or missing transaction timestamps instead of allowing invalid date math
- **Background Kill Switches**: Added worker-side write controls so optional telemetry and optional game-code writes can be disabled quickly during incidents without shipping a new extension package
- **Worker Response Hardening**: Standardized worker error responses to stable codes and tightened payload-size handling for background endpoints
- **Strict Platform Segregation**: Confirmed and enforced separate Chrome/Firefox worker endpoints and D1 stores for optional cloud features
- **Operational Fail-Safe Behavior**: Optional telemetry and game-code services now follow deterministic outage behavior to avoid leaking internals in error responses

### Fixed
- **Timezone Day Rendering**: Corrected off-by-one date display when formatting day keys (`YYYY-MM-DD`) in some timezones
- **Dashboard Polish**: Improved results-page control consistency and reduced UI clutter
- **Platform Backend Isolation**: Firefox now points to Firefox-specific worker endpoints for telemetry and game-code operations (separate from Chrome)
- **Game Code Outage Messaging**: Game-code generation now shows a clear temporary-unavailability message when the bridge service is intentionally disabled
- **Totals Regression Guardrails**: Incomplete refreshes now preserve stable complete-type data instead of silently replacing it with smaller partial subsets
- **First-Run Reliability**: Added bounded recovery for abnormal pagination stops to reduce cases where users need to manually retry
- **Retry Targeting Accuracy**: Incomplete-data retry now consistently focuses on unresolved fetch segments and reports recovery outcomes more clearly

### Changed
- **Top 10 Purchases Context Localization**: Replaced hardcoded English context with locale key wiring across all language packs
- **Completeness Banner Visibility**: Incomplete-data banner now uses sticky behavior to stay visible while scrolling through results
- **Login Safety Wording**: Updated security copy to state that Roblox Rewind does not display an in-extension login screen and does not collect credentials; users sign in on Roblox's official website
- **Localization Copy Consistency**: Aligned login/security wording between UI fallback text and i18n source keys to keep translated and fallback copy in sync
- **Privacy Policy Update**: Updated privacy documentation to reflect background safety controls and operational handling for optional cloud features
- **Fetch Reliability Statusing**: Added lightweight run-status reporting and clearer retry outcome summaries for incomplete-data recovery
- **Aggregate Reliability Telemetry**: Added aggregate-only fetch reliability events (completion state, stop-reason counts, retry outcomes) without sending personal or transaction content

---

## [0.3.5] - 2026-02-15

### Added
- **Settings Menu**: Added a small top-right settings menu with a language picker and accessibility options (high contrast, reduced motion, larger text). Preferences are saved locally and apply immediately
- **More Languages**: Added additional language options and locale support for Arabic (Modern Standard + Egypt), Bengali, Marathi, Nigerian Pidgin, Tamil, Telugu, Urdu, and Cantonese (Yue)
- **Category Spending Drilldown**: "Spending by Category" is now an interactive donut chart with a clickable legend and an in-panel breakdown of top purchases per category
- **Yearly Spending Drilldown**: "Yearly Spending" now includes a per-year breakdown panel with top purchases, and you can click bars (or use the year selector) to switch years

### Security
- **Host Permission Least Privilege**: Replaced wildcard Roblox host permission with explicit required domains only
- **XSS Surface Reduction**: Disabled `data-i18n-html` translation path and replaced Fun Facts dynamic card rendering with `textContent`-based DOM creation
- **Worker Hardening**: Telemetry and game-bridge Workers now validate origin and request payloads more strictly before storing data

### Changed
- **Privacy Documentation Accuracy**: Updated README and privacy copy to explicitly document optional telemetry and optional game-code cloud transfer behavior
- **Login Safety Copy**: Clarified in the Data Privacy modal that Roblox Rewind does not show an in-extension login form and never collects credentials
- **Drilldown List Length**: Yearly and category drilldowns now show a maximum of 7 items for readability
- **Robux From Money Clarity**: Added a small breakdown line showing Robux purchases vs Premium/BC subscription stipends for better context and layout consistency
- **Sharper Chart Labels**: Chart text is now snapped to device pixels for crisper rendering on high-DPI and scaled displays
- **Membership History Redesign**: Membership History is now a year-by-year month grid with a details panel, making Premium vs Builders Club periods easier to read

### Fixed
- **Cache Clearing Scope**: "Clear Cache" now removes only Rewind cache keys instead of wiping all extension storage
- **Cache Identity Verification**: Cached results are now only auto-loaded and reused when you're logged into the same Roblox account they were fetched from
- **Analysis Memoization**: Fixed `analyzeSpending()` caching so results aren't recomputed repeatedly when opening share/export features
- **Sort Toggle Performance**: Fixed repeated event handler binding on sort buttons that could cause duplicate re-renders over time
- **Export Memory Leak**: Export now revokes temporary download URLs after use
- **Startup Cache Race**: Prevented cached auto-display from clobbering an in-progress refresh
- **Fun Facts Date Hardening**: Guarded against malformed or missing transaction timestamps to prevent crashes and incorrect break/spree calculations
- **Day-Key Date Formatting**: Fixed off-by-one day display when formatting `YYYY-MM-DD` day keys in some timezones
- **Charts Grid Layout**: Yearly + Category sections now balance height cleanly without leaving awkward dead space
- **Comparison Unit Price Rendering**: Fixed language override placeholder formatting that could strip `$`-prefixed values (e.g. unit price/min wage sublabels)
- **Translation Coverage**: Real-world comparisons, breakdown labels, drilldowns, empty states, and share/copy feedback now translate correctly when switching languages
- **Modal Translation Coverage**: "How does this work?" and "What about my data?" modal body text is now fully localized when switching languages
- **Nigerian Pidgin Coverage**: Completed translation pass so the Nigerian Pidgin language pack is no longer mostly English
- **Locale Encoding Repair**: Fixed corrupted translation characters that could appear as `?` in some languages
- **Locale-Aware Formatting**: Dates and numbers now format using the selected language/locale
- **Incomplete Data Banner Visibility**: The incomplete data banner now stays visible while scrolling so it's harder to miss while viewing insights
- **Accessibility - Larger Text**: Larger text mode now visibly scales the dashboard UI
- **Refresh Button Localization**: Refresh/Retry loading state no longer overrides translations and uses a subtle spinner indicator
- **Zero-Spend Identity Localization**: Account-age zero-spend messages now translate and pluralize correctly across languages
- **Membership Detection**: Improved stipend detection and ensured Premium tiers are only inferred after the Premium launch date to avoid incorrect Premium/BC classification
- **Fun Facts Clarity**: Clarified ambiguous Fun Facts (Top 10 Purchases, Longest Spending Spree, Longest Break, Peak Hour, Top Weekday, Shopping Days), fixed creator counting for "Unique Creators", and made "Biggest Purchase" + "First Item Purchase" more self-explanatory

---

## [0.3.4] - 2026-02-06

### Added
- **More Real-World Comparisons**: More variety in spending comparisons - items are now randomized each visit instead of showing the same three every time
- **Comparison Price Labels**: Each comparison item now shows its unit price (e.g. "at $5.50 each") for context, fully translated in all 10 languages
- **Zero-Purchase Handling**: Accounts with no spending history now show a friendly message instead of empty sections, with different messages based on account age
- **Anonymous Usage Data**: Optional anonymous telemetry to help improve the extension - tracks basic events like load success and fetch duration, with no personal data collected. Opt out anytime from the privacy modal
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
- **Removed Web Accessible Resources**: Extension resources are no longer web-accessible since no external pages need them - tighter security surface

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
- **Cache Duration Setting**: Users can now choose how long to keep transaction data cached (1 hour, 6 hours, 24 hours, or 1 week) via Advanced Features -> Cache Duration
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
