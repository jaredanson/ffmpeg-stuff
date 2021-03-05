# ffmpeg-stuff

### settings

* crf (0-51) default 23, 0 is lossless
* preset (slow/medium/fast) more options https://gist.github.com/asus4/f5aef0f3f46fde198436da12f0332013
* [tune](#tune-settings)
* hide_banner


## cut video without encoding

`./ffmpeg.exe -i input.mp4 -c copy -ss 00:21:06 -to 00:24:24 output.mp4 `

## 265 encoding no gpu

`./ffmpeg.exe -i input.mp4 -vcodec libx265 -crf 23 -c:a copy -c:s copy output.mp4`


## x264 gpu

`./ffmpeg.exe -vsync 0 -hwaccel cuda -hwaccel_output_format cuda -i input.mp4 -c:a copy -c:v h264_nvenc -c:s copy -crf 23 output.mp4 `

## hevc/265 gpu

` ./ffmpeg.exe -vsync 0 -hwaccel cuda -hwaccel_output_format cuda -i input.mp4 -c:a copy -c:v hevc_nvenc -c:s copy -crf 23 -preset slow output.mp4 `

## youtube-dl and ffmpeg

` youtube-dl https://www.youtube.com/watch?v=BaW_jenozKc --postprocessor-args "-c:v libx265 -preset slow -crf 23 -c:a copy -c:s copy" --merge-output-format mp4 `

### tune settings

```
    film – use for high quality movie content; lowers deblocking
    animation – good for cartoons; uses higher deblocking and more reference frames
    grain – preserves the grain structure in old, grainy film material
    stillimage – good for slideshow-like content
    fastdecode – allows faster decoding by disabling certain filters
    zerolatency – good for fast encoding and low-latency streaming
    psnr – ignore this as it is only used for codec development
    ssim – ignore this as it is only used for codec development 
```
