# Roblox Rewind - Privacy Policy
**Last updated: March 17, 2026**

## Overview

Roblox Rewind is a browser extension that analyzes your Roblox spending history. Your privacy is important.

## What Data We Access

When you use Roblox Rewind, the extension can access:
- Your Roblox username and user ID
- Your Roblox transaction history (for example purchases, Robux spending, Premium/BC stipends, sales, payouts, and trades)
- Your Roblox avatar thumbnail (for display and share image generation)

If you choose **Generate Game Code**, the extension also creates a limited summary payload from your analyzed results.

This data is accessed directly from Roblox using your existing logged-in browser session. Core analysis happens locally on your device.

## APIs Used

### Roblox APIs (Official)
- `users.roblox.com/v1/users/authenticated` - Gets your authenticated Roblox user
- `economy.roblox.com/v2/users/{userId}/transactions` - Fetches transaction history
- `thumbnails.roblox.com/v1/users/avatar-headshot` - Gets avatar thumbnails
- `www.roblox.com/headshot-thumbnail/image` - Fallback avatar thumbnail URL

### External APIs
- `api.frankfurter.app/latest?from=USD` - Exchange rates for localized comparisons (cached for 24 hours)
- Cloudflare Worker `/events` endpoint - Receives optional anonymous usage events
- Cloudflare Worker `/rewind` endpoint - Receives optional game-code summary payloads

## How Your Data Is Used

Roblox data is used to:
- Calculate spending totals
- Generate charts, breakdowns, and insights
- Create shareable summary images

Optional anonymous usage events are used to improve reliability and performance.

If you choose **Generate Game Code**, a limited summary is uploaded so it can be loaded in the connected Roblox game by code (**currently in beta**).

## Where Data Is Stored

### Local storage on your device
- `robloxRewindCache`: Cached Roblox transaction dataset and fetch metadata
- `cacheDurationPreference`: Your selected cache duration
- `rewindSettings`: Language, accessibility, performance, compare-mode, and digest-view preferences
- `telemetryOptOut`: Your anonymous usage-data preference
- `localStorage` key `robloxRewindExchangeRates`: Cached exchange-rate data

### Cloud storage (only for optional features)
- Anonymous usage events (if enabled) are stored in Cloudflare D1 via the telemetry Worker
- Game-code payloads (if you generate a code) are stored in Cloudflare D1 via the game-bridge Worker
- During security or reliability incidents, optional cloud endpoints may be temporarily disabled (for example, game-code generation) until service health is restored

Telemetry events do **not** include your Roblox username, user ID, raw transaction history, cookies, or session tokens.

## Anonymous Usage Data (Optional)

If enabled, the extension may send minimal anonymous events such as:
- Load started/completed
- Authentication failure
- Fetch duration and rate-limit counts
- Stage timing totals (for example auth/cache/fetch/retry/analysis/render durations)
- Aggregate compare/digest interaction events (for example compare open/switch/use, digest open/use)
- Session timing summaries (for example total session time and aggregate section-open duration)
- Share image saved
- Data export triggered

These events may include:
- Extension version
- UI locale/language
- Aggregate diagnostic fields (for example total transaction count, cache hit flag, timing/retry counters, render profile, device class bucket, selected performance mode, selected share layout/theme, compare interaction count, and digest-open duration)

Retention:
- Anonymous usage events are retained in telemetry storage until deleted during operational maintenance/purges

You can opt out at any time:
**Advanced Features -> What about my data? -> Anonymous Usage Data** (toggle off).

## Game Code Sharing (Optional)

If you click **Generate Game Code**, Roblox Rewind sends a limited summary payload to the game-bridge Worker so it can be loaded by the connected Roblox game (**currently in beta**).

This payload can include:
- Total USD estimate
- Total Robux spent and purchased
- Transaction count and membership months
- Top category and top purchase summary

It does **not** include full transaction history.

Retention behavior:
- Codes are random
- Codes are configured to expire after about 24 hours
- Payloads are intended to be removed after successful retrieval

## What We Do Not Collect

- Passwords or login credentials
- Payment card or banking details
- Personal communications
- Browsing history outside extension functionality
- Roblox cookies or session tokens

## Third-Party Sharing

We do not sell user data.

Optional telemetry and optional game-code payloads are processed by Cloudflare Workers and stored in Cloudflare D1 only for extension functionality described above.

## Data Deletion

To clear cached Roblox data in the extension:
1. Open the extension
2. Click **Advanced Features**
3. Click **Clear Cache**

To stop sending new optional anonymous usage events:
1. Open the extension
2. Click **Advanced Features**
3. Click **What about my data?**
4. Turn off **Anonymous Usage Data**

This clears Rewind cache data used for analysis and exchange-rate cache data. Preference settings (for example language/accessibility and telemetry opt-out) are retained unless you uninstall the extension.

Uninstalling the extension removes extension-local stored data.

## Footnote on Game Availability

The connected Roblox game used with **Generate Game Code** is currently in beta and has not had a full public release yet. Availability, access, and behavior may change while beta testing continues.

## Contact

If you have questions about this policy:
- Ko-fi: https://ko-fi.com/cosisety
- Email: ProfessionalCosisety@gmail.com

## Changes

If this policy changes, an updated version will be posted with a new "Last updated" date.
