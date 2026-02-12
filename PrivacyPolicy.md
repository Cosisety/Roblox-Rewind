# Roblox Rewind - Privacy Policy
**Last updated: February 11th, 2026**

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
- Cloudflare Worker `/rewind` endpoint - Used only when you choose **Generate Game Code** for Roblox game integration

## How Your Data Is Used

Your data is used solely to:
- Calculate your total spending
- Generate spending breakdowns and charts
- Create shareable summary images

Anonymous usage statistics (if enabled) are used only to improve reliability and performance.
If you choose **Generate Game Code**, a limited Rewind summary is uploaded so it can be loaded inside the Roblox game by code.

## Where Your Data Is Stored

**Your Roblox data stays on your device.**

- Transaction data is cached locally in your browser (default 1 hour, configurable)
- Anonymous telemetry events (if enabled) are stored in Cloudflare D1
- Game code payloads are stored temporarily in Cloudflare D1 only when you generate a game code
- The UI shows your current cache duration so you can verify the setting

Telemetry events do **not** include your username, user ID, transaction history, or cookies.

Game code payloads are short-lived and contain summary fields only (for example totals and top category/item), not your full transaction history.

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

You can opt out at any time:
**Advanced Features -> Data Privacy -> Anonymous Usage Data** (toggle off).

## Game Code Sharing (Optional)

If you click **Generate Game Code**, Roblox Rewind sends a small summary payload to a Cloudflare Worker so the Roblox game can load your snapshot.

This payload can include:
- Total USD estimate
- Total Robux spent / purchased
- Transaction count and membership months
- Top category and top purchase summary

Protection and retention:
- Codes are random and one-time use
- Codes expire after 24 hours
- Successful retrieval deletes the code payload

## What We Don't Collect

- Passwords or login credentials
- Payment methods or credit card information
- Personal communications
- Browsing history outside of Roblox transaction data
- Roblox cookies or session tokens

## Third-Party Sharing

**We do not sell, trade, or transfer your data to anyone.**

Anonymous usage events (if enabled) and optional game-code payloads are processed by Cloudflare Workers and stored in Cloudflare D1.

## Data Deletion

To delete all cached data:
1. Open the extension
2. Click "Advanced Features"
3. Click "Clear Cache"

Uninstalling the extension removes all locally stored data. If you opt out of anonymous usage data, no new usage events are sent.
Previously generated game codes automatically expire within 24 hours and are deleted after successful use.

## Contact

If you have questions about this privacy policy, you can reach me at:
- Ko-fi: https://ko-fi.com/cosisety
- Email: ProfessionalCosisety

## Changes

If this policy changes, the updated version will be posted here with a new date.
