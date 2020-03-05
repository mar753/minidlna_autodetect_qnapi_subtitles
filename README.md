# Download QNapi subtitles as UTF-8 with BOM (for miniDLNA)

If you are using Raspberry Pi Zero as a DLNA server (miniDLNA) and using QNapi for subtitle downloading you may encounter some issues with SRT subtitle recognition. If you change options to download SRT file in UTF-8 format, there is one small issue with it - this UTF-8 file does not contain BOM header (`0xEFBBBF`), thus miniDLNA will not recognize this subtitle file at all. 
Because of those issues there was this `napi` bash script created which can be pasted to `/usr/local/bin` and then run in a folder with a movie using command:
`napi <movie_file>`

It will use QNapi to download subtitles and then convert them to UTF-8 with BOM header, this way we will fetch subtitles which will be recognized by miniDLNA and enjoy our movie with the subtitles. Remember to change QNapi options to download subtitles as SRT and conversion of the downloaded subtitles should be set to UTF-8 format.
