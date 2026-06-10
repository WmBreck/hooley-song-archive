# Supabase Plan

Purpose:
Supabase will store structured archive data for Hooley the Poet.

Initial storage buckets:
- song-images
- song-audio
- documents

Future main tables:
- projects
- songs
- assets
- collections
- song_versions

Design principle:
Files live in storage. Supabase tables store descriptions, links, relationships, and publishing metadata.

Do not rush table creation. The database should follow the creative workflow.