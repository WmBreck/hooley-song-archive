Songs Table

Purpose:

The songs table stores the master record for each Hooley the Poet song.

A song should exist independently of any particular album, playlist, website, book, or video project.

Core Fields

* id
* song_id
* title
* slug
* alternate_titles
* lyricist
* status
* genre
* mood
* themes
* lyrics
* notes
* created_at
* updated_at

Publishing Links

* suno_url
* soundcloud_url
* youtube_url
* tiktok_url

Release Information

* release_status
* release_date
* credits
* copyright_notes

Asset Relationships

* primary_cover_asset_id

Project Relationships

* primary_project_id

Status Values

* idea
* draft
* revised
* finished
* published
* archived

Design Principle

Songs are the core creative works.

Audio files, images, prompts, videos, playlists, books, and website pages should be linked to songs rather than replacing the song record itself.
