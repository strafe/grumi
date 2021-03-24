# grumi
> 🖼️ Upload an image, video or album to Imgur via the command line.

## Dependencies
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
    -c, --client_id         Imgur Client ID (overrides ${HOME}/.config/grumi/client_id).
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
<br>

Once submitted you'll be given a `Client ID` and `Client secret`. Copy the `Client ID` and place it in `$HOME/.config/grumi/client_id` (you can also use the `-c, --client_id` option instead of the local file if it fits your use case).

## Restrictions
Imgur impose some harsher restrictions on API uploads compared to their website uploader:
- The following MIME types are supported:
  - Images: `image/jpeg`, `image/gif`, `image/apng`, `image/tiff` & `image/png`.
  - Videos: `video/mp4`, `video/webm`, `video/x-matroska`, `video/quicktime`, `video/x-flv`, `video/x-msvideo`, `video/x-ms-wmv` & `video/mpeg`.
- Images are limited to 10MB in file size, and videos are limited to 200MB in file size.
- Videos are limited to 60 seconds in length.

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
