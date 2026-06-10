# Data Import Plan

## Goal

Move the current master song catalog and downloaded-song data into the Hooley the Poet repository so future work can continue from a durable source of truth.

## Current Priority

Do not import the data blindly.

Before importing, the archive needs a clear staging structure so raw data, cleaned data, and final database-ready data do not get confused.

## Recommended Repository Structure

Use three levels of data:

- data/raw
- data/processed
- data/import-ready

## Definitions

### data/raw

Original exports or spreadsheets exactly as received.

Do not edit these files except to replace them with a newer export.

### data/processed

Cleaned working files created from the raw data.

These may include normalized titles, extracted metadata, duplicate detection, and preliminary matching.

### data/import-ready

Final files prepared for Supabase import.

These should match the planned database structure as closely as possible.

## First Import Targets

Start with CSV files or JSON files representing:

- songs
- song_versions
- assets
- collections
- collection_items

## Required Cleanup Before Supabase Import

Before creating real Supabase records, the data should be reviewed for:

- duplicate song titles
- multiple versions of the same song
- missing titles
- missing lyrics
- missing source links
- SoundCloud playlist membership
- Best Of Hooley selections
- downloaded file names that do not clearly match song titles

## Best Of Hooley Matching

The Best Of Hooley playlist should be treated as a curated signal.

When possible, each playlist item should be matched to:

- the underlying song
- the selected song version
- the SoundCloud URL
- play count or public response data
- cover image if available

## Import Principle

The initial import should preserve evidence rather than force certainty.

If two versions might be the same song but the match is uncertain, preserve that uncertainty in notes or match_status fields.

## Suggested Match Status Values

- confirmed
- likely_match
- possible_match
- duplicate_candidate
- unresolved

## Near-Term Next Steps

1. Add the current master song catalog file to data/raw.
2. Preserve the original file without editing it.
3. Create a processed version for cleanup and matching.
4. Identify the Best Of Hooley playlist items.
5. Match playlist items to downloaded song/version records.
6. Only then prepare Supabase import files.

## Long-Term Goal

The imported data should support:

- lyric book creation
- electronic book links
- song version comparison
- custom pitch playlists
- AI-assisted lyric review
- story-behind-the-song notes
- future HooleyThePoet.com pages
