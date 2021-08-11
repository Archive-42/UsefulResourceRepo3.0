## <a href="#media-manipulation-cheat-sheet" class="w-toc__header--link">Media manipulation cheat sheet</a>

- [Display characteristics](#display-characteristics)
- [Demux (split) audio and video](<#demux-(split)-audio-and-video>)
- [Shaka Packager](#shaka-packager)
- [FFmpeg](#ffmpeg)
- [Change characteristics](#change-characteristics)
- [Bitrate](#bitrate)
- [Dimensions (resolution)](<#dimensions-(resolution)>)
- [File type](#file-type)
- [Synchronize audio and video](#synchronize-audio-and-video)
- [Codec](#codec)
- [Packager](#packager)
- [DASH/MPD](#dashmpd)
- [HLS](#hls)
- [Clear Key Encryption](#clear-key-encryption)
- [Create a key](#create-a-key)
- [Encrypt](#encrypt)
- [Create a key information file](#create-a-key-information-file)
- [Encrypt for HLS](#encrypt-for-hls)
- [Widevine Encryption](#widevine-encryption)
- [Media conversion sequence](#media-conversion-sequence)
- [DASH/WebM with Shaka Packager](#dashwebm-with-shaka-packager)
- [DASH/MP4 with Shaka Packager](#dashmp4-with-shaka-packager)
- [Widevine](#widevine)
- [HLS/MP4](#hlsmp4)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Media manipulation cheat sheet

Sep 20, 2018 <span class="w-author__separator">•</span> Updated Sep 24, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

This page offers these resources:

- Commands for manipulating specific characteristics of media files.
- The sequence of commands needed to get from a raw mov file to encrypted media assets.

Conversion is done with these applications:

- [Shaka Packager](https://github.com/google/shaka-packager) ([on Stack Overflow](https://stackoverflow.com/questions/tagged/shaka))
- [FFmpeg](https://ffmpeg.org/download.html), version 4.2.2-tessus ([on Stack Overflow](https://stackoverflow.com/questions/tagged/ffmpeg))
- [OpenSSL](https://www.openssl.org/) ([on Stack Overflow](https://stackoverflow.com/questions/tagged/openssl))

Although I've tried to show equivalent operations for all procedures, not all operations are possible in both applications.

In many cases, the commands I'm showing may be combined in a single command line operation, and in actual use would be. For example, there's nothing preventing you from setting an output file's bitrate in the same operation as a file conversion. For this cheat sheet, I often show these operations as separate commands for the sake of clarity.

Please let me know of useful additions or corrections. [Pull requests are welcome](/media-cheat-sheet).

This page contains a few more commands than are covered in this section. Not only are there plans to cover these topics (we have drafts already), we also hope this page will be a resource for multiple levels of expertise.

## Display characteristics <a href="#display-characteristics" class="w-headline-link">#</a>

    packager input=myvideo.mp4 --dump_stream_info

    ffmpeg -i myvideo.mp4

Technically, FFmpeg always requires an output file format. Calling FFmpeg this way will give you an error message explaining that; however, it lists information not available using Shaka Packager.

## Demux (split) audio and video <a href="#demux-(split)-audio-and-video" class="w-headline-link">#</a>

Shaka Packager requires demuxing when converting files. This is also required for using media frameworks.

### Shaka Packager <a href="#shaka-packager" class="w-headline-link">#</a>

**_MP4_**

    packager input=myvideo.mp4,stream=video,output=myvideo_video.mp4
    packager input=myvideo.mp4,stream=audio,output=myvideo_audio.m4a

Or:

    packager \
      input=myvideo.mp4,stream=video,output=myvideo_video.mp4 \
      input=myvideo.mp4,stream=audio,output=myvideo_audio.m4a

**_WebM_**

    packager \
      input=myvideo.webm,stream=video,output=myvideo_video.webm \
      input=myvideo.webm,stream=audio,output=myvideo_audio.webm

### FFmpeg <a href="#ffmpeg" class="w-headline-link">#</a>

**_MP4_**

    ffmpeg -i myvideo.mp4 -vcodec copy -an myvideo_video.mp4
    ffmpeg -i myvideo.mp4 -acodec copy -vn myvideo_audio.m4a

**_WebM_**

    ffmpeg -i myvideo.webm -vcodec copy -an myvideo_video.webm
    ffmpeg -i myvideo.webm -acodec copy -vn myvideo_audio.webm

## Change characteristics <a href="#change-characteristics" class="w-headline-link">#</a>

### Bitrate <a href="#bitrate" class="w-headline-link">#</a>

For FFmpeg, I can do this while I'm converting to mp4 or WebM.

    ffmpeg -i myvideo.mov -b:v 350K myvideo.mp4
    ffmpeg -i myvideo.mov -vf setsar=1:1 -b:v 350K myvideo.webm

### Dimensions (resolution) <a href="#dimensions-(resolution)" class="w-headline-link">#</a>

    ffmpeg -i myvideo.webm -s 1920x1080 myvideo_1920x1080.webm

### File type <a href="#file-type" class="w-headline-link">#</a>

Shaka Packager cannot process mov files and hence cannot be used to convert files from that format.

**_mov to MP4_**

    ffmpeg -i myvideo.mov myvideo.mp4

**_mov to WebM_**

    ffmpeg -i myvideo.mov myvideo.webm

### Synchronize audio and video <a href="#synchronize-audio-and-video" class="w-headline-link">#</a>

To ensure that audio and video synchronize during playback, insert keyframes.

    ffmpeg -i myvideo.mp4 -keyint_min 150 -g 150 -f webm -vf setsar=1:1 out.webm

### Codec <a href="#codec" class="w-headline-link">#</a>

The tables below list common containers and codecs for both audio and video, as well as the FFmpeg library needed for conversion. A conversion library must be specified when converting files using FFmpeg.

#### Video <a href="#video" class="w-headline-link">#</a>

<table><thead><tr class="header"><th>Codec</th><th>Container</th><th>Library</th></tr></thead><tbody><tr class="odd"><td>av1</td><td>mkv</td><td>libaom-av1</td></tr><tr class="even"><td></td><td>WebM</td><td>libaom-av1</td></tr><tr class="odd"><td>h264</td><td>MP4</td><td>libx264</td></tr><tr class="even"><td>vp9</td><td>WebM</td><td>libvpx-vp9</td></tr></tbody></table>

#### Audio <a href="#audio" class="w-headline-link">#</a>

<table><thead><tr class="header"><th>Codec</th><th>Container</th><th>Library</th></tr></thead><tbody><tr class="odd"><td>aac</td><td>MP4</td><td>aac</td></tr><tr class="even"><td>opus</td><td>WebM</td><td>libopus</td></tr><tr class="odd"><td>vorbis</td><td>WebM</td><td>libvorbis</td></tr></tbody></table>

**_MP4/H.264_**

    ffmpeg -i myvideo.mp4 -c:v libx264 -c:a copy myvideo.mp4

**_Audio for an MP4_**

    ffmpeg -i myvideo.mp4 -c:v copy -c:a aac myvideo.mp4

**_WebM/VP9_**

    ffmpeg -i myvideo.webm -v:c libvpx-vp9 -v:a copy myvideo.webm

**_Audio for a WebM_**

    ffmpeg -i myvideo.webm -v:c copy -v:a libvorbis myvideo.webm
    ffmpeg -i myvideo.webm -v:c copy -v:a libopus myvideo.webm

## Packager <a href="#packager" class="w-headline-link">#</a>

### DASH/MPD <a href="#dashmpd" class="w-headline-link">#</a>

Dynamic Adaptive Streaming over HTTP is a [web-standards-based](https://developer.mozilla.org/en-US/docs/Web/HTML/DASH_Adaptive_Streaming_for_HTML_5_Video) method of presenting video-on-demand for the web.

    packager \
      input=myvideo.mp4,stream=audio,output=myvideo_audio.mp4 \
      input=myvideo.mp4,stream=video,output=myvideo_video.mp4 \
      --mpd_output myvideo_vod.mpd

### HLS <a href="#hls" class="w-headline-link">#</a>

HTTP Live Streaming (HLS) is [Apple's standard](https://developer.apple.com/streaming/) for live streaming and video on demand for the web.

    ffmpeg -i myvideo.mp4 -c:a copy -b:v 8M -c:v copy -f hls -hls_time 10 \
            -hls_list_size 0 myvideo.m3u8

## Clear Key Encryption <a href="#clear-key-encryption" class="w-headline-link">#</a>

### Create a key <a href="#create-a-key" class="w-headline-link">#</a>

You can use the same method to create a key for both DASH and HLS. Do this using [openssl](https://www.openssl.org/). The following will create a key made of 16 hex values.

    openssl rand -out media.key 16

This command creates a file with white space and new line characters, which are not allowed by Shaka Packager. You'll need to open the key file and manually remove all whitespace including the final carriage return.

### Encrypt <a href="#encrypt" class="w-headline-link">#</a>

For the `-key` flag use the key created earlier and stored in the media.key file. However, when entering it on the command line, be sure you've removed its whitespace. For the `-key_id` flag repeat the key value.

    packager \
      input=myvideo.mp4,stream=audio,output=glocka.m4a \
      input=myvideo.mp4,stream=video,output=glockv.mp4 \
      --enable_fixed_key_encryption \
      -key INSERT_KEY_HERE -key_id INSERT_KEY_ID_HERE \

### Create a key information file <a href="#create-a-key-information-file" class="w-headline-link">#</a>

To encrypt for HLS you need a key information file in addition to a key file. A key information file is a text file with the format below. It should have the extension `.keyinfo`. For example: `encrypt.keyinfo`.

    key URI
    key file path
    private key

The key URI is where the `media.key` ([created above](#create-a-key) will be located on your server. The key file path is it's location relative to the key information file. Finally, the private key is the contents of the `media.key` file itself. For example:

    https://example.com/media.key
    /path/to/media.key
    8b4c39c498949536

### Encrypt for HLS <a href="#encrypt-for-hls" class="w-headline-link">#</a>

    packager \
      'input=input.mp4,stream=video,segment_template=output$Number$.ts,playlist_name=video_playlist.m3u8' \
      'input=input.mp4,stream=audio,segment_template=output_audio$Number$.ts,playlist_name=audio_playlist.m3u8,hls_group_id=audio,hls_name=ENGLISH' \
      --hls_master_playlist_output="master_playlist.m3u8" \
      --hls_base_url="http://localhost:1000/"

This command will accept a key with either 16 or 32 characters.

    ffmpeg -i myvideo.mov -c:v libx264 -c:a aac -hls_key_info_file key_info myvideo.m3u8

## Widevine Encryption <a href="#widevine-encryption" class="w-headline-link">#</a>

    packager \
      input=glocken.mp4,stream=video,output=enc_video.mp4 \
      input=glocken.mp4,stream=audio,output=enc_audio.m4a \
      --enable_widevine_encryption \
      --key_server_url "https://license.uat.widevine.com/cenc/getcontentkey/widevine_test" \
      --content_id "Hex_converted_unique_ID" --signer "widevine_test" \
      --aes_signing_key "1ae8ccd0e7985cc0b6203a55855a1034afc252980e970ca90e5202689f947ab9" \
      --aes_signing_iv "d58ce954203b7c9a9a9d467f59839249"

## Media conversion sequence <a href="#media-conversion-sequence" class="w-headline-link">#</a>

This section shows in order commands needed to get from a raw mov file to encrypted assets packaged for DASH or HLS. For the sake of having a goal to illustrate, I'm converting my source file to a bitrate of 8Mbs at a resolution of 1080p (1920 x 1080). Adjust these values as your needs dictate.

### DASH/WebM with Shaka Packager <a href="#dashwebm-with-shaka-packager" class="w-headline-link">#</a>

Not all steps are possible with Shaka Packager, so I'll use ffmpeg when I need to.

1.  Convert the file type and codec.

    For this command you can use either `liborbis` or `libopus` for the audio codec.

        ffmpeg -i glocken.mov -c:v libvpx-vp9 -c:a libvorbis -b:v 8M -vf setsar=1:1 -f webm glocken.webm

2.  Create a Clear Key encryption key.

    You'll need to open the key file and manually remove all whitespace including the final carriage return.

        openssl rand -out media.key 16

3.  Demux (separate) the audio and video, encrypt the new files, and output a media presentation description (MPD) file.

    The `-key` and `-key_id` flags are copied from the `media.key` file.

        packager \
          input=myvideo.webm,stream=video,output=myvideo_video.webm \
          input=myvideo.webm,stream=audio,output=myvideo_audio.webm \
          --enable_fixed_key_encryption --enable_fixed_key_decryption \
          -key INSERT_KEY_HERE -key_id INSERT_KEY_ID_HERE \
          --mpd_output myvideo_vod.mpd

4.  Remux (recombine) the audio and video streams. If you're using a video framework, you may not need to do this.

        ffmpeg -i mymovie.mp4 -i myaudio.m4a -c copy finalmovie.mp4

### DASH/MP4 with Shaka Packager <a href="#dashmp4-with-shaka-packager" class="w-headline-link">#</a>

Not all steps are possible with Shaka Packager, so I'll use ffmpeg when I need to.

1.  Convert the file type, video codec and bitrate.

    The default pixel format, yuv420p is used because one isn't supplied in the command line. The app will give you an error message that it is deprecated. I've chosen not to override the default because, though deprecated yuv420p is the most widely supported.

        ffmpeg -i mymovie.mov -c:v libx264 -c:a aac -b:v 8M -strict -2 mymovie.mp4

2.  Create a Clear Key encryption key.

    You'll need to open the key file and manually remove all whitespace including the final carriage return.

        openssl rand -out media.key 16

3.  Demux (separate) the audio and video, encrypt the new files, and output a media presentation description (MPD) file.

    The `-key` and `-key_id` flags are copied from the `media.key` file.

        packager \
          input=mymovie.mp4,stream=audio,output=myaudio.m4a \
          input=mymovie.mp4,stream=video,output=myvideo.mp4 \
          --enable_fixed_key_encryption --enable_fixed_key_decryption \
          -key INSERT_KEY_HERE -key_id INSERT_KEY_ID_HERE \
          --mpd_output myvideo_vod.mpd

4.  Remux (recombine) the audio and video streams. If you're using a video framework, you may not need to do this.

        ffmpeg -i mymovie.mp4 -i myaudio.m4a -c copy finalmovie.mp4

### Widevine <a href="#widevine" class="w-headline-link">#</a>

The two previous examples used Clear Key encryption. For widevine the final two steps are replaced with this.

Everything in this command except the name of your files and the `--content-id` flag should be copied exactly from the example. The `--content-id` is 16 or 32 random hex digits. Use the keys provided here instead of your own. (This is how Widevine works.)

1.  Demux (separate) the audio and video, encrypt the new files, and output a media presentation description (MPD) file.

        packager \
          input=mymovie.mp4,stream=audio,output=myaudio.m4a \
          input=mymovie.mp4,stream=video,output=myvideo.mp4 \
          --enable_widevine_encryption \
          --key_server_url "https://license.uat.widevine.com/cenc/getcontentkey/widevine_test" \
          --content_id "fd385d9f9a14bb09" --signer "widevine_test" \
          --aes_signing_key "1ae8ccd0e7985cc0b6203a55855a1034afc252980e970ca90e5202689f947ab9" \
          --aes_signing_iv "d58ce954203b7c9a9a9d467f59839249"

2.  Remux (recombine) the audio and video streams. If you're using a video framework, you may not need to do this.

        ffmpeg -i mymovie.mp4 -i myaudio.m4a -c copy finalmovie.mp4

### HLS/MP4 <a href="#hlsmp4" class="w-headline-link">#</a>

HLS only supports MP4, so first you'll need to convert to the MP4 container and supported codecs. Not all steps are possible with Shaka Packager, so I'll use FFmpeg when I need to.

1.  Convert the file type, video codec, and bitrate.

    The default pixel format, yuv420p, is used because one isn't supplied in the command line. The app will give you an error message that it is deprecated. I've chosen not to override the default because, though deprecated yuv420p is the most widely supported.

        ffmpeg -i mymovie.mov -c:v libx264 -c:a aac -b:v 8M -strict -2 mymovie.mp4

2.  Create a Clear Key encryption key.

    You'll need to open the key file and manually remove all whitespace including the final carriage return.

        openssl rand -out media.key 16

3.  Create a key information file

        packager \
          'input=input.mp4,stream=video,segment_template=output$Number$.ts, \
            playlist_name=video_playlist.m3u8' \
              'input=input.mp4,stream=audio,segment_template=output_audio$Number$.ts, \
            playlist_name=audio_playlist.m3u8,hls_group_id=audio,hls_name=ENGLISH' \
              --hls_master_playlist_output="master_playlist.m3u8" \
              --hls_base_url="http://localhost:1000/" \
              --enable_fixed_key_encryption --enable_fixed_key_decryption \
              -key INSERT_KEY_HERE -key_id INSERT_KEY_ID_HERE \

<a href="/tags/media/" class="w-chip">Media</a> <a href="/tags/audio/" class="w-chip">Audio</a>

<span class="w-mr--sm">Last updated: Sep 24, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/media-cheat-sheet/index.md)

<a href="/media" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

- ### Contribute

  - <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
  - <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

- ### Related content

  - <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
  - <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
  - <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
  - <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
  - <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
  - <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

- ### Connect

  - <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
  - <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

- <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
- <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
- <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
- <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

- <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
- <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
