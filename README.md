# AutoBleep (formerly known as Bleep It!)

This library/tool is just a thin wrapper around [whisper_timestamped](https://github.com/linto-ai/whisper-timestamped) and [ffmpeg](https://ffmpeg.org/).

It was made for a very specific use case. If you think we can improve general usability via better commands and help docs, please create an Issue and/or Pull Request.

The way it works is by passing it a video file. Any video file supported by `ffmpeg` will work. It will then output an audio only file for you to bring into your video editor of choice.

## Prerequisites

Most of this library's documentation assumes `pip` and `pipenv` with python3 to be installed. You will also need ffmpeg.

- python3
- pip https://pypi.org/project/pip/
- pipenv https://pipenv.pypa.io/en/latest/#install-pipenv-today
- ffmpeg https://ffmpeg.org

No testing has been done without these requirements. If you would like to see docs for other tools/etc please create an issue or PR.

## Installation

### Using Pip

```
pip install git+https://github.com/cmgriffing/autobleep.git
```

### Using Pipenv
Clone the repo.

Use this to establish the pipfile-based python env:

```
pipenv shell
```
```
pipenv install
```

The `Locking...` step can take a while. If you would like to use the locked version of dependencies you can use:

```
pipenv install --ignore-pipfile
```

## Usage

### If Installed With Pip
```
autobleep --input=./examples/example1.mkv --output=./output/output.mka
```

Or do it with a custom JSON file containing words to bleep.
```
autobleep --input=./examples/example1.mkv --output=./output/output.mka --swear_words=./examples/bleep.json
```


### If Installed With Pipenv
The current way of running the application is to use this command in your pipenv shell:

```
python3 ./main.py --input=./examples/example1.mkv --output=./output/output.mka
```

Or do it with a custom JSON file containing words to bleep.
```
python3 ./main.py --input=./examples/example1.mkv --output=./output/output.mka --swear_words=./examples/bleep.json
```

Make sure to replace the input and output files with your own values.

### Docker
If you are unable to install neccessary dependencies you may try running docker command instead as follows:

```bash
docker run --rm -it -v "$(pwd)/examples/example1.mkv:/input/input.mkv" -v "$(pwd)/output:/output" autobleep/bleep
```

User permissions no worked out full and may need to own output with `chown ./output/output.mka`

## Roadmap

This script was put together quickly to accomplish one specific workflow. It would be nice to improve this app in several ways.

- Bundled dependencies: `python3` and `ffmpeg` are the big dependencies that are required at the OS level. `whisper_timestamped` is the main python dependency. Bundling all of this into a single portable executable would be very nice.

- UI: A UI in which you could fine tune the placement of "bleeps" would be nice.

- Video Editor plugins: If portability/bundling can be achieved it would be nice to have this functionality exist within your video editor of choice as a plugin.

## Contributing

This project uses black for formatting the code.

Install the package with its development dependencies. This makes sure you are developing with the same version as the github actions workflows.

```
pip install "autobleep[dev] @ git+https://github.com/cmgriffing/autobleep.git"
```

## License

Copyright 2023 Chris Griffing

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
