# Roblox Rewind - Privacy Policy
**Last updated: February 7th, 2026**

## Overview

Roblox Rewind is a browser extension that analyzes your Roblox spending history. Your privacy is important.

## What Data We Access

When you use Roblox Rewind, the extension reads:
- Your Roblox username and user ID
- Your Roblox transaction history (purchases, Robux spending, Premium/BC stipends)
- Your Roblox avatar (for share images)

This data is accessed directly from Roblox.com using your existing logged-in browser session. All analysis happens locally on your device.

## APIs Used

### Roblox APIs (Official)
- `users.roblox.com/v1/users/authenticated` - Gets your username and user ID
- `economy.roblox.com/v2/users/{userId}/transactions` - Fetches your transaction history
- `thumbnails.roblox.com/v1/users/avatar-headshot` - Gets your avatar for the share image

### External APIs
- `api.frankfurter.app/latest?from=USD` - Free exchange rate API for localized comparisons (cached 24 hours)
- Cloudflare Worker `/events` endpoint - Receives **anonymous usage statistics** if enabled

## How Your Data Is Used

Your data is used solely to:
- Calculate your total spending
- Generate spending breakdowns and charts
- Create shareable summary images

Anonymous usage statistics (if enabled) are used only to improve reliability and performance.

## Where Your Data Is Stored

**Your Roblox data stays on your device.**

- Transaction data is cached locally in your browser (default 1 hour, configurable)
- No Roblox transaction details or account identifiers are stored in the cloud
- The UI shows your current cache duration so you can verify the setting

If anonymous usage data is enabled, event counts are stored in a Cloudflare D1 database. These events do **not** include your username, user ID, transaction data, or cookies.

## Anonymous Usage Data (Optional)

If enabled, the extension sends minimal, anonymous events such as:
- Whether a data load started or completed
- Whether authentication failed
- Aggregate fetch timing and rate-limit counts
- Whether a share image was saved
- Whether a data export was performed

These events include only:
- Extension version
- UI language (locale)

You can opt out at any time.

## What We Don't Collect

- Passwords or login credentials
- Payment methods or credit card information
- Personal communications
- Browsing history outside of Roblox transaction data
- Roblox cookies or session tokens

## Third-Party Sharing

**We do not sell, trade, or transfer your data to anyone.**

Anonymous usage events (if enabled) are processed by Cloudflare Workers and stored in Cloudflare D1.

## Data Deletion

To delete all cached data:
1. Open the extension
2. Click "Advanced Features"
3. Click "Clear Cache"

Uninstalling the extension removes all locally stored data. If you opt out of anonymous usage data, no new usage events are sent.

## Contact

If you have questions about this privacy policy, you can reach me at:
- Ko-fi: https://ko-fi.com/cosisety
- Email: ProfessionalCosisety

## Changes

If this policy changes, the updated version will be posted here with a new date.
