# grumi
> 🖼️ Upload an image, video or album to Imgur via the command line.

## Dependencies
- [file](https://linux.die.net/man/1/file)
- [curl](https://curl.haxx.se/)
- [jq](https://stedolan.github.io/jq)

## Installation
- macOS
```
brew install strafe/tap/grumi
```

- Linux
	- You know what you're doing :penguin:.

## Usage
```
Usage: grumi [OPTIONS] <file1> <file2>...
Upload an image, video or album to Imgur.

Options:
    -h, --help              Output this message.
    -v, --version           Output the current version.
    -a, --album             Creates an album containing the provided image(s)/video(s).
    -c, --client_id         Imgur Client ID (overrides ${HOME}/.grumi).
    -d, --disable_audio     Disables audio in provided videos.
```

## Examples
Upload a single image or video (videos may take a while to process).
```
$ grumi image.png
grumi: https://i.imgur.com/abcdef.png (image.png)

$ grumi video.mp4
grumi: https://i.imgur.com/ghijkl.mp4 (video.mp4)
```

Upload multiple files at once.
```
$ grumi image.png video.mp4
grumi: https://i.imgur.com/abcdef.png (image.png)
grumi: https://i.imgur.com/ghijkl.mp4 (video.mp4)
```

Upload multiple files to an album.
```
$ grumi -a image.png video.mp4
grumi: https://imgur.com/a/mnopqr
```

Upload an image by URL.
```
$ grumi https://example.com/example.png
grimi https://i.imgur.com/abcdef.png (example.png)
```

Upload a video without audio.
```
$ grumi -d video.mp4
grumi: https://i.imgur.com/ghijkl.mp4 (video.mp4)
```

## License
[MIT](LICENSE)
