# bulk-compress-media-windows
注意压缩视频的时候，你可以需要微调一下`-crf 28`这个参数，这个值约小质量越好。4K/1080P的视频用28质量不错，720P可能要调整到26或者24甚至更低。

# 🎞️ Windows Batch Media Processor

A lightweight, self-contained Windows `.bat` script that recursively processes all images and videos in a directory using **FFmpeg**.

✔ Images are compressed and normalized to **JPEG**
✔ Videos are re-encoded to **H.265 (HEVC)**
✔ Original files are replaced in-place
✔ Temporary files are avoided
✔ Full runtime summary (images, videos, total files, elapsed time)
✔ Handles invalid paths gracefully
✔ Works on Windows 7–11

---

## 🚀 Features

### 🖼 Image Processing

* Supports: `.jpg`, `.jpeg`, `.png`, `.bmp`, `.tiff`, `.webp`
* Converts each image to:
  **JPEG + quality=4 (ffmpeg -q:v 4)**
* Replaces original files with the processed version

### 🎥 Video Processing

* Supports: `.mp4`, `.mkv`, `.avi`, `.flv`, `.mov`, `.wmv`, `.m4v`
* Converts each video to H.265/HEVC using:

  ```
  -c:v libx265 -crf 28 -tag:v hvc1
  -c:a copy
  -map_metadata 0
  ```
* Ensures metadata is preserved
* Avoids reprocessing temporary files (`_temp.jpg`, `_temp.mp4`)

### ⏱ Runtime Summary

The script prints:

```
Processed Images:  XXX
Processed Videos:  XXX
Total Files:       XXX
Total Time:        HH:MM:SS.CC
```

### 🛡 Safe & Stable

* Silently skips invalid paths
* Uses WMIC for robust timestamp extraction
* No dependencies besides **FFmpeg**

---

## 📦 Requirements

* **Windows** 7/8/10/11
* **FFmpeg** installed and added to PATH

  > Download from: [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)

To check if FFmpeg is available:

```bat
ffmpeg -version
```

---

## 📁 How to Use

1. Place the `.bat` file in the root directory containing your images/videos
2. Double-click to run
3. The script will:

   * Recursively scan all subfolders
   * Process supported media files
   * Replace originals
   * Print a summary when done

---

## 🧾 License

Feel free to modify, distribute, and use for any personal or commercial project.

---

## ⭐ Contributions

Issues and PRs are welcome if you want to optimize, add new formats, or extend the summary output.

