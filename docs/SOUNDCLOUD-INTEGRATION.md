# SoundCloud Integration

## Credentials Storage

Do NOT store the SoundCloud Client Secret in GitHub.

Store credentials in a secure password manager and later in Supabase secrets/environment variables.

## Redirect URIs

Development Redirect URI:

http://localhost:3000/auth/soundcloud/callback

Planned Production Redirect URI:

https://hooleythepoet.com/auth/soundcloud/callback

## API Facts

- Base API URL: https://api.soundcloud.com
- Auth URL: https://secure.soundcloud.com
- Authentication: OAuth 2.1 with PKCE
- API requests use an Authorization header with an OAuth access token
- Access tokens expire and must be refreshed
- Public resource metadata can use the client credentials flow
- User-specific actions require authorization code flow

## Initial Goals

- Connect SoundCloud playlists
- Import track metadata
- Track playlist membership
- Sync play counts and engagement metrics
- Match SoundCloud tracks to songs and song versions

## First Practical Feature

The first integration feature should be read-only:

Paste or store a SoundCloud playlist URL, then resolve it through the API and import track metadata.

This should support the Best Of Hooley playlist first.

## Read-Only Metadata to Capture

For each SoundCloud track, capture:

- SoundCloud track ID
- title
- permalink URL
- artwork URL
- duration
- description
- play count
- likes count
- comment count
- created date
- sharing or access status
- playlist membership
- last synced timestamp

## Proposed Supabase Tables

### soundcloud_tracks

Stores track metadata from SoundCloud.

Likely fields:

- id
- soundcloud_track_id
- title
- permalink_url
- artwork_url
- duration_ms
- description
- playback_count
- likes_count
- comment_count
- access
- raw_json
- last_synced_at
- created_at
- updated_at

### soundcloud_playlists

Stores SoundCloud playlist or set metadata.

Likely fields:

- id
- soundcloud_playlist_id
- title
- permalink_url
- description
- artwork_url
- track_count
- raw_json
- last_synced_at
- created_at
- updated_at

### soundcloud_playlist_items

Links SoundCloud playlists to SoundCloud tracks.

Likely fields:

- id
- soundcloud_playlist_id
- soundcloud_track_id
- position
- raw_json
- created_at
- updated_at

### soundcloud_sync_log

Records sync attempts and errors.

Likely fields:

- id
- sync_type
- source_url
- status
- records_seen
- records_created
- records_updated
- error_message
- started_at
- finished_at

## Relationship to Main Archive

SoundCloud data should not replace the main archive.

SoundCloud should be treated as the public-performance and publication metadata source.

The Hooley archive remains the source of truth for:

- lyrics
- story behind the song
- personal significance
- book inclusion
- version selection
- revision notes
- AI review notes

## Matching Strategy

SoundCloud tracks should later be matched to song_versions, not directly to songs.

Reason:
One song may have multiple SoundCloud uploads, each with a different cover image, duration, title variant, or play count.

Suggested future matching fields:

- soundcloud_track_id
- song_version_id
- match_status
- match_confidence
- match_notes

Suggested match_status values:

- confirmed
- likely_match
- possible_match
- unresolved
- duplicate_candidate

## Future Workflow

SoundCloud API -> Supabase Edge Function -> Supabase Tables -> HooleyThePoet.com

## Security Notes

- Client ID may be referenced in configuration when needed.
- Never commit the Client Secret to GitHub.
- Keep OAuth secrets server-side only.
- Store tokens and refresh tokens only in secure server-side storage.

## Development Sequence

1. Keep credentials in a password manager.
2. Add redirect URIs in the SoundCloud app settings.
3. Store secrets in Supabase when ready.
4. Create read-only Supabase tables for SoundCloud metadata.
5. Build an Edge Function for resolving a playlist URL.
6. Import the Best Of Hooley playlist first.
7. Match SoundCloud tracks to existing raw catalog rows.
8. Match confirmed tracks to song_versions.
9. Use SoundCloud play counts and playlist membership as evidence, not as final artistic judgment.
