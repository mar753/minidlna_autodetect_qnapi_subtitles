# Download QNapi subtitles and automatically detect change on the miniDLNA server

If you are using miniDLNA on Raspberry Pi (Zero) as a DLNA server and using QNapi for subtitle downloading - as UTF-8 SRT (can be read by VLC or Kodi - Android TV), you may encounter some issues with the donwloaded subtitle file recognition. miniDLNA server uses `inotify` (must be enabled in the miniDLNA's config) to detect changes in our filesystem, but for some reason it will not see the new `*.srt` file created by QNapi. To fix this issue I have created a script called `napi` which wraps:
- QNapi execution
- creates from the downloaded SRT file a new SRT temporary file with the UTF-8 BOM header (`0xEFBBBF`) added (just in case)
- removes originally downloaded SRT file and then renames the temporary one (with BOM) to the original filename
There is no need to add a BOM header, you can just make a copy of the originally downloaded SRT file, remove originally downloaded file and rename the copy to the originally downloaded filename.
Only in this way miniDLNA will detect your new subtitle file and you will not have to run `sudo minidlnad -R` & `sudo service minidlna restart` manually.

You can paste the `napi` file directly to `/usr/local/bin` to use the command globally in your terminal using:
`napi <movie_file>`.

Remember to change QNapi options to download subtitles as SRT and conversion of the downloaded subtitles should be set to UTF-8 format.
