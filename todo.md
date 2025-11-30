- [ ] Fix issues with seek not working for certain media types like mkv
  - **Analysis**: MKV seeking issues are a known Chromium/HTML5 video limitation. The video element struggles with containers that lack proper keyframe indices.
  - **Current status**: Range requests are properly implemented in the media protocol handler.
  - **Potential solutions**: 
    1. Use ffmpeg to remux MKV to MP4 on-the-fly (resource intensive)
    2. Pre-process videos with `ffmpeg -i input.mkv -c copy -movflags +faststart output.mp4`
    3. Document as known limitation for certain poorly-encoded MKV files
- [x] Add support for customization of seek eg using shift + arrow keys for larger increments default (30 seconds)
  - **Implemented**: Shift + Arrow keys now seek 30 seconds, regular arrow keys seek 10 seconds
  - **Shortcuts display updated** in the settings menu
- [X] Building this app for windows completes successfully however the generated executable does not complete the installation processes sometimes it just launches and vanishes without any error. It doesn't show in the task manager to be kind of running in the background. Need to investigate this issue.
  - **Fixes applied**:
    1. Added `asarUnpack` config for native modules (better-sqlite3, ffmpeg-static, ffprobe-static)
    2. Deferred database initialization until app is ready
    3. Added comprehensive error handling and logging to `%APPDATA%/kino/kino-debug.log`
    4. Added global exception handlers to catch and log crashes
  - **Next steps**: Rebuild and test. Check `kino-debug.log` if issues persist.
- [x] So there's something wrong with clearing the already existing playlist. I clear it and its still shows the previous playlist items.When I click the refresh button it shows the previous items again. Need to fix this issue.
  - **Root cause**: The "Refresh playlists" button calls `generateDefaultPlaylists()` which auto-creates playlists based on folder names. When a playlist was deleted, refreshing would recreate it.
  - **Fix applied**:
    1. Added `deleted_folder_playlists` table to track user-deleted folder playlists
    2. When a playlist is deleted, its name is stored in the deleted list
    3. `generateDefaultPlaylists()` now skips folders that are in the deleted list
    4. Manually creating a playlist with the same name clears it from the deleted list

  - [x] Deleted watch folders still showed movies in the library after removal
    - **Root cause**: Removing a watch path only deleted the path from `watch_paths` but did not remove movies whose `file_path` lived under that folder.
    - **Fix applied**:
      1. Added `removeMoviesByWatchPath(watchPath)` to the database layer to delete movies whose `file_path` starts with the removed watch path.
      2. Added `getWatchPathById(id)` helper to retrieve the path before deletion.
      3. Updated the `db:remove-watch-path` IPC handler to call `removeMoviesByWatchPath` before removing the watch path.

  - [x] Thumbnails and local media failed to load with `media://` URLs (Windows paths)
    - **Symptoms**: Requests like `media://C:\Users\...\thumbnails\153.jpg` returned `net::ERR_UNEXPECTED` and poster images fell back to a network placeholder which failed when offline.
    - **Root cause**: Windows paths with spaces and backslashes weren't URL-encoded when constructing `media://` URLs.
    - **Fix applied**:
      1. Use `encodeURIComponent()` when constructing `media://` URLs in the renderer (poster and video src).
      2. The main process protocol handler uses `decodeURIComponent()` and now correctly resolves the decoded Windows path and serves range requests.

  - [x] External placeholder image caused network error when offline
    - **Fix applied**: Replaced external `via.placeholder.com` fallback with an inline SVG data URI and added image-error state handling to avoid network dependency.