# Song Versions Table

Purpose:
The song_versions table tracks each distinct recorded or published version of a song.

This is essential because one song may have many versions, and different versions may perform differently on SoundCloud or be better suited for different uses.

## Why This Table Matters

The archive must distinguish between:

- the underlying song
- a specific Suno generation or audio version
- a specific SoundCloud upload
- the version selected for The Best Of Hooley playlist
- the version selected for a book, website, pitch playlist, or video

Without this distinction, duplicate versions will be hard to manage.

## Proposed Fields

- id
- song_id
- version_title
- version_label
- version_number
- platform
- platform_url
- source_file_name
- duration
- play_count
- likes_count
- comments_count
- cover_asset_id
- is_best_of_version
- is_book_version
- is_pitch_version
- quality_notes
- performance_notes
- selection_reason
- created_at
- updated_at

## Example Version Labels

- original
- revised
- acoustic
- smooth
- country
- duet
- female_vocal
- male_vocal
- orchestral
- best_of_soundcloud
- book_selected

## Design Notes

A song version is not the same thing as a song.

For example, Misery Loves Company may be one song, but it may have several versions with different vocals, arrangements, covers, links, and play counts.

SoundCloud performance should be stored as useful evidence, not treated as final proof of quality.

A version may perform better because of the recording, the cover image, the SoundCloud algorithm, timing, playlist placement, or luck.

## Future Uses

This table should support:

- matching downloaded files to SoundCloud versions
- identifying the Best Of Hooley version
- selecting book links
- comparing duplicate versions
- building custom pitch playlists
- tracking which versions have the best public response
