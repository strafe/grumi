# grumi
> 🖼️ Upload an image, video or album to Imgur via the command line.

## Dependencies
- [`file`](https://linux.die.net/man/1/file)
- [`curl`](https://curl.haxx.se/)
- [`jq`](https://stedolan.github.io/jq)

## Installation
- macOS (`jq` will be automatically installed)
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

## Setup
`grumi` requires you to provide your own Client ID to authenticate with the Imgur API. This is **not** used to associate uploads with your account, but simply to access the API.

To generate one, register a new application with Imgur [here](https://api.imgur.com/oauth2/addclient). The fields listed below are **required**. What you choose to provide is mostly up to you, as ***Authorization type*** is the only important field.
Field|Value
-|-
_Application name_|`grumi`
_Authorization type_|`Anonymous usage without user authentication`
_Authorization callback URL_|`example.com`
_Email_|`grumi@example.com`

Once submitted you'll be given a `Client ID` and `Client secret`. Copy the `Client ID` and place it in `$HOME/.grumi` (you can also use the `-c, --client_id` option instead of the local file if it fits your use case).

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
