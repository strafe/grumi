# grumi
> 🖼️ Upload an image, video or album to Imgur.

## Dependencies
- [file](https://linux.die.net/man/1/file)
- [curl](https://curl.haxx.se/)
- [jq](https://stedolan.github.io/jq)
- [ffprobe](https://www.ffmpeg.org/ffprobe.html) (video only)

## Installation
- macOS
```
brew tap strafe/tap
brew install grumi
```

- Linux
	- You know what you're doing :penguin:.


## Usage
```
Usage: grumi [OPTIONS] <image1> <image2>...
Upload an image, video or album to Imgur.

Options:
    -h, --help              Output this message.
    -v, --version           Output the current version.
    -c, --client_id         Imgur Client ID (overrides ${HOME}/.grumi).
    -d, --disable_audio     Disables audio in passed videos.
    -a, --album             Create an album containing the passed images/videos.
```

## Examples
Upload a single image or video.
```
$ grumi image.png
https://i.imgur.com/abcdef.png

$ grumi video.mp4
https://i.imgur.com/ghijkl.mp4
```

Upload multiple files at once.
```
$ grumi image.png video.mp4
https://i.imgur.com/abcdef.png
https://i.imgur.com/ghijkl.mp4
```

Upload multiple files to an album.
```
$ grumi -a image.png video.mp4
https://imgur.com/a/mnopqr
```

Upload a video without audio.
```
$ grumi -d video.mp4
https://i.imgur.com/ghijkl.mp4
```

## License
[MIT](LICENSE)
