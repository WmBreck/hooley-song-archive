# Projects Table

Purpose:
The projects table will organize Hooley the Poet work into larger creative or publishing containers.

A project can be:
- an album
- a playlist
- a musical
- a songbook
- a video series
- a promotional campaign
- a standalone major song project

## Proposed Fields

- id
- project_title
- project_slug
- project_type
- status
- short_description
- long_description
- primary_audience
- public_visibility
- start_date
- release_date
- notes
- created_at
- updated_at

## Example Project Types

- album
- playlist
- musical
- book
- video
- single_song
- website_section
- promotional_campaign

## Design Notes

Projects are the top-level containers. Songs, images, audio, documents, prompts, and videos can later be connected to one or more projects.

This prevents the archive from becoming only a song list. It supports future uses such as HooleyThePoet.com, SoundCloud collections, YouTube videos, TikTok promotions, printed songbooks, and musical theater projects.
