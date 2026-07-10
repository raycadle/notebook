---
tags:
  - computers/servers/home
  - library/media/management
---
# Media Management

This document outlines the organizational procedures of the media library.

The library is categorized by type, and a full list of media in each can be found below:
- [[_Utilities/Templates/Shows]]
- [[_Utilities/Templates/Movies]]
- [[Music]]
- [[Books]]

File's name and metadata are updated to reflect the correct information.

## Formats

The filename and metadata formats are outlined below.

See [[#Editing Metadata]] for a list of used editors.

### Shows

Shows is a mix of eastern animation (anime), western animation (cartoons), and live-action shows.

##### Format

Show Name/Season XX/Part XX/Show Name - SXXEXX

**Example:**
Black Lagoon/Season 01/Black Lagoon - S01E13.mkv

##### Required Metadata

- Title
- Dual Audio (English & Japanese, if available)
- Subtitles (English, if available)

***

### Movies

Movies is a mix of live-action and animation. Multi-part movies are grouped into collections.

##### Format

Movie Name (YYYY)/Movie Name (YYYY).mkv

**Example:**
Lucy (2014)/Lucy (2014).mkv

#### Collections

Collections are groups of movies with one or more sequels.
Grouped in a single directory, with subdirectories containing each sequel.
'Collection' is appended to the directory name.

##### Collection Format

Collection Name/(YYYY) Movie Name/Movie Name (YYYY).mkv

**Example:**
Fast and Furious Collection/(2006) The Fast and the Furious: Tokyo Drift/The Fast and the Furious: Tokyo Drift (2006).mkv 

##### Required Metadata

- Title
- Dual Audio (English & Japanese, if available)
- Subtitles (English, if available)

***

### Music

##### Filename Format

Artist Name/(YYYY) Artist Name - Album Name/XX. Song Title (ft. Feature Artist 1; Feature Artist 2).mp3

**Example:**
Big Sean/(2020) Big Sean - Detroit 2/13. Full Circle (ft. Key Wayne; Diddy).mp3

##### Required Metadata

- Title
- Artist
- Album
- Album Artist
- Release Year
- Genre
- Track Number
- Disk Number (if multiple disks)
- Cover Picture
- Lyrics (synced & plain, if available)

***

### Books

##### Format

Author Name/Series Title/Author Name - Book Title.epub

**Example:**
Robert Kiyosaki/Robert Kiyosaki - Rich Dad, Poor Dad.epub

##### Required Metadata

- Title
- Author
- Release Year
- Series (if available)
- Cover (original if available)

***

## Tools

Tools for organizing media files.

### Renaming Files

- Bulky (bulk file renamer)
- Epiname (episode title script)

### Editing Metadata

| Media Type | Tool |
| --- | --- |
| **Music** | [kid3](https://kid3.kde.org/)
| **Video** | [mkvtoolnix](https://mkvtoolnix.download/)
| **Book** | [calibre](https://calibre-ebook.com/)
