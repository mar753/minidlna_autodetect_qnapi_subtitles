# Download QNapi subtitles as UTF-8 with BOM (for miniDLNA)

I was using Raspberry Pi Zero as my DLNA server (miniDLNA) and I was using QNapi for subtitle downloading. I changed options to download SRT file in UTF-8 format, but there is one small issue with it - this UTF-8 file does not contain BOM header (`0xEFBBBF`), thus miniDLNA will not recognize this subtitle file at all. 
So I created this `napi` bash script which can be pasted to `/usr/local/bin` and then run in a folder with a movie using command:
`napi <movie_file>`

It will use QNapi to download the subtitles and then convert them to UTF-8 with BOM header, this way we will fetch subtitles which will be recognized by miniDLNA and enjoy our movie with subtitles. Remember to change QNapi options to download subtitles as SRT and conversion of a downloaded subtitles should be set to UTF-8 format.
