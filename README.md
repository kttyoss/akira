![Akira header](https://cdn.bone.lol/images/ktty/Akira.jpg)
## Akira - The simple image processor
Akira is a simple image processor that takes a single HTTP POST request with two form data inputs - size and image - and returns an array of images in those sizes in Base64 format.

## Installation
Installing Akira is simple! Simply clone the repository and run `docker build` then run.
```bash
git clone https://github.com/kttyoss/akira
cd akira
docker build --tag akira .
docker run -d -p 8000:8000 akira
```

You can also download Akira from the [Docker Hub](https://hub.docker.com/r/embedbblz/akira)
```bash
docker pull embedbblz/akira
docker run -d -p 8000:8000 embedbblz/akira
```

## Usage
To use Akira, send a POST request to the `/resize` endpoint with `size` and `image` form data inputs. The size accepts multiple parameters and is formatted with a `;` in between each size. 
```bash
curl -X POST -F 'size=64x64;128x128' -F 'image=@/path/to/image.jpg' http://localhost:8000/resize
```

Akira will return a JSON response that includes an array of images with their size and the image encoded as a base64 string.

```json
{
	"images": [
		{
			"size": "64x64",
			"base64": "data:image/jpeg;base64,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"
		},
		{
			"size": "128x128",
			"base64": "data:image/jpeg;base64,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"
		}
	],
	"error": false
}
```

## Contributing

Contributions to Akira are welcome! To contribute, fork this repository, make your changes, and submit a pull request.

## License

Akira is licensed under the GNU General Public License v3.0. See [LICENSE](https://github.com/kttyoss/akira/blob/master/LICENSE) for more information.
