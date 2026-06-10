# SoundCloud Integration

## Credentials Storage

Do NOT store the SoundCloud Client Secret in GitHub.

Store credentials in a secure password manager and later in Supabase secrets/environment variables.

## Redirect URIs

Development Redirect URI:

http://localhost:3000/auth/soundcloud/callback

Planned Production Redirect URI:

https://hooleythepoet.com/auth/soundcloud/callback

## Initial Goals

- Connect SoundCloud playlists
- Import track metadata
- Track playlist membership
- Sync play counts and engagement metrics
- Match SoundCloud tracks to songs and song versions

## Future Workflow

SoundCloud API -> Supabase Edge Function -> Supabase Tables -> HooleyThePoet.com

## Security Notes

- Client ID may be referenced in configuration when needed.
- Never commit the Client Secret to GitHub.
- Keep OAuth secrets server-side only.
