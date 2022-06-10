# README

3つのストリームがあります。

## 元のストリーム（HLS with ts）

このリポジトリ上にはないです。

https://bitdash-a.akamaihd.net/content/MI201109210084_1/m3u8s/f08e80da-bf1d-4e3d-8899-f0f6155f6efa.m3u8

## 元のストリームをffmpegでMP4に再エンコードしたもの

`bitdash.mp4`

以下のコマンドで作成しました
```
ffmpeg -i https://bitdash-a.akamaihd.net/content/MI201109210084_1/m3u8s/f08e80da-bf1d-4e3d-8899-f0f6155f6efa.m3u8  bitdash.mp4
```

## ffmpegでmp4から再エンコードしたもの（HLS with ts）

`manifest.m3u8`

ストリームの特性というよりは、配信されているサーバが同じでありサーバの遅延差によるラグではないことを証明するために置いています。

```
ffmpeg -i bitdash.mp4 -c copy -hls_time 10 -hls_playlist_type vod -hls_segment_filename "video%3d.ts" manifest.m3u8
```

