# ffmpeg-stuff

### settings

* global_quality (0-51) recommend around 21, 0 is lossless
* preset (veryslow 1/slower 2/slow 3/medium 4/fast 5/faster 6/veryfast 7) 0 to 7 (default 0)
* [tune](#tune-settings)
* hide_banner

## intel arc

`av1_qsv, h264_qsv, hevc_qsv, vp9_qsv`


## cut video without encoding

`./ffmpeg.exe -i input.mp4 -c copy -ss 00:21:06 -to 00:24:24 output.mp4 `

## 265 encoding no gpu

`./ffmpeg.exe -i input.mp4 -vcodec libx265 -global_quality 23 -c:a copy -c:s copy output.mp4`


## x264 gpu

`./ffmpeg.exe -hwaccel qsv -hwaccel_output_format qsv -i input.mp4 -fps_mode passthrough -c:a copy -c:v h264_qsv -c:s copy -global_quality 21 output.mp4 `

## hevc/265 gpu

` ./ffmpeg.exe -hwaccel qsv -hwaccel_output_format qsv -i input.mp4 -fps_mode passthrough -c:a copy -c:v hevc_qsv -c:s copy -global_quality 21 -preset slow output.mp4 `

## av1 gpu

` ./ffmpeg.exe -hwaccel qsv -hwaccel_output_format qsv -i input.mp4 -fps_mode passthrough -c:a copy -c:v av1_qsv -c:s copy -global_quality 21 -preset slow output.mp4 `

## youtube-dl and ffmpeg

` youtube-dl https://www.youtube.com/watch?v=BaW_jenozKc --postprocessor-args "-c:v libx265 -preset slow -global_quality 21 -c:a copy -c:s copy" --merge-output-format mp4 `

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
