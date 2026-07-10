# Media Manager Notes

### ✅ Features To Implement or Look For

1. **Metadata Scraping & Tagging**

   * Uses APIs to fetch metadata from sources like:

     * **Movies/TV**: [TMDb](https://www.themoviedb.org/), [IMDb](https://www.imdb.com/), [TVDB](https://thetvdb.com/)
     * **Music**: [MusicBrainz](https://musicbrainz.org/), [Last.fm](https://www.last.fm/)
     * **Books**: [Google Books API](https://developers.google.com/books), [Open Library](https://openlibrary.org/developers)
     * **Manga/Comics**: [AniList](https://anilist.co/), [MyAnimeList](https://myanimelist.net/apiconfig), [ComicVine](https://comicvine.gamespot.com/api/)

2. **Media Identification**

   * File parsing using `guessit`, `hachoir`, or regular expressions to deduce the title, year, season/episode, etc.

3. **Tagging and Renaming**

   * Using `mutagen`, `eyed3`, or `python-mediainfo` for audio files.
   * Rename and move files to a structured directory.

4. **Custom Operation Scheme**

   * YAML/JSON configuration file that lets users specify:

     * Directory structure
     * Naming conventions
     * Which metadata source to prioritize

5. **Cross-Platform File Management**

   * Platform-agnostic design for Windows, macOS, Linux.

---

### 📦 Example Tools / Libraries to Build or Use

#### 1. **[FileBot](https://www.filebot.net/)** (Java-based, GUI and CLI)

* Excellent for movies and TV shows
* Can be controlled via scripts (you could automate via Python subprocess)

#### 2. **[Beets](https://beets.io/)** (Python-based, for Music)

* Metadata tagging, renaming, plugins
* Can be extended/customized with plugins

#### 3. **[LazyLibrarian](https://github.com/DobyTang/LazyLibrarian)** (for books/comics)

* Automates management and tagging of books, magazines, and comics
* Can fetch metadata from multiple sources

#### 4. **Custom Python Script**

You can create a unified script like this (pseudo-skeleton):

```python
# Example: Unified Media Library Organizer (skeleton)

import os
from configparser import ConfigParser
from media_modules import movie_handler, music_handler, book_handler

# Load configuration
config = ConfigParser()
config.read('config.ini')

# Walk through media directory
for root, dirs, files in os.walk(config['paths']['media_root']):
    for file in files:
        filepath = os.path.join(root, file)
        if file.endswith(('.mp4', '.mkv')):
            movie_handler.process(filepath, config)
        elif file.endswith(('.mp3', '.flac')):
            music_handler.process(filepath, config)
        elif file.endswith(('.epub', '.pdf', '.cbz')):
            book_handler.process(filepath, config)
```

Each `handler` module can:

* Use a third-party API to get metadata
* Rename/move the file
* Optionally update embedded tags

---

### 🧩 Modular Design Suggestion

* `config.ini` or `config.yaml`: User settings
* `media_modules/`

  * `movie_handler.py`
  * `music_handler.py`
  * `book_handler.py`
  * `comic_handler.py`
  * `utils.py`: helper functions (e.g., API calls, file renaming)

---

### ✅ Bonus Features (Optional)

* **Logging & dry-run mode**
* **GUI with `tkinter` or `PyQt`**
* **Scheduled jobs (via cron or Task Scheduler)**