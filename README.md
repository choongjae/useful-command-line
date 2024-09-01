# useful-command-line

A repository of random command line tools/utilities that I found to be useful, along with any specific useful commands for them that serve common use cases.

## [ffmpeg](https://ffmpeg.org/)
My uses for ffmpeg have been very simple (webp -> mp4) or (opus -> mp3), so I've barely scratched the surface on what it can do. Of course, there's always [HandBrake](https://handbrake.fr/) as a GUI-friendly option.

### useful commands

- m3u8 into mp4 (per [StackOverflow](https://stackoverflow.com/questions/32528595/ffmpeg-mp4-from-http-live-streaming-m3u8-file))  
  `ffmpeg -i "FILE_URL" -c copy -bsf:a aac_adtstoasc "OUTPUT_FILENAME.mp4"`

## [yt-dlp](https://github.com/yt-dlp/yt-dlp)
yt-dlp bypasses the risk of using random online Youtube downloaders, while also giving so many more options wrt downloading multiple videos (playlist) at once, filtering out files that would exceed a size limit, choosing to download only the audio or video (both together or separated), subtitling, formatting, encoding, and et cetera. It also has support for [far more sites than just Youtube](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md), though I've only used it with Youtube so far.

### useful commands

- download only audio  
  `yt-dlp -x "FULL_URL"`
- download a video from Youtube with H264 encoding (per [Reddit](https://www.reddit.com/r/youtubedl/wiki/h264/))
  - Option 1: This downloads the video as an mp4 with the original H264 encoding stored on Youtube, but it will only allow the resultant video to be max 1080p  
    `yt-dlp -f "bv*[vcodec^=avc]+ba[ext=m4a]/b[ext=mp4]/b" "FULL_URL"`
  - Option 2: This downloads the file and then yt-dlp reencodes it to be mp4 using H264. Note that there are restrictions depending on what the audio file is encoded as; see the Reddit link for more detail, but this should work for most Youtube videos.  
    `yt-dlp --recode mp4 "FULL_URL"`
