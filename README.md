# [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](#) OST Generator 


This script allows you to download and merge YouTube playlist videos into a single file using [yt-dlp](https://github.com/yt-dlp/yt-dlp) and [ffmpeg](https://ffmpeg.org/download.html). Ensure that you have them installed before running.


## Usage

### Step 1: Create a Directory (Optional but Recommended)
Since this script downloads all videos into the current folder, it's recommended to create a dedicated directory first:

```bash
mkdir playlist_name && cd playlist_name
```

### Step 2: Download Videos from a YouTube Playlist
Run the following command to download all videos in the best available format (change `playlist_url` as you please):

```bash
yt-dlp -f bestvideo+bestaudio -o "%(autonumber)s.%(ext)s" "https://www.youtube.com/playlist?list=PLBKadB95sF45NmJNNFnqgal8d8uUluUii"
```

### Step 3: Concatenate the Downloaded Videos
After downloading, run the following command to generate a `filelist.txt` and concatenate the videos into a single file:

#### Windows (Command Prompt):
```bash
(for %f in (*.webm) do @echo file '%f') > filelist.txt
ffmpeg -f concat -safe 0 -i filelist.txt -c copy output.webm
del filelist.txt
```

#### Linux/macOS (Bash):
```bash
for f in *.webm; do echo "file '$f'" >> filelist.txt; done
ffmpeg -f concat -safe 0 -i filelist.txt -c copy output.webm
rm filelist.txt
```

## Notes
- The output format is `.webm`, but you can modify the script to use other formats.
- Ensure that all videos are in the same codec for `ffmpeg` to concatenate them without re-encoding.

## License
This project is open-source and free to use. Modify as needed!

