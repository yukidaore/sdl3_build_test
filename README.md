## About

SDL3 の一連のライブラリを CMakeLists.txt 一発で DL&ビルドするテストプロジェクト。

SDL3+SDL_image を一括ビルドしたあとに、
それを参照するサンプルアプリ(SDL_image の showimage サンプル)をビルドする。

## ビルド

```bash
$ cd sdl3_test_app/
$ cmake -S . build
$ cmake --build build
```

## テスト実行

```bash
$ ./build/Debug/sdl3_test_app.exe ./test_image.gif
$ ./build/Debug/sdl3_test_net.exe google.com  
$ ./build/Debug/sdl3_test_mixer.exe jingle_23.mp3 jingle_25.mp3   
```

## 注意

vcpkgを参照する環境ではテストしてないので、オプショナルパッケージを有効にしたビルドは未確認。
以下のようなメッセージが出る状態だけど、とりあえず用意した確認用サンプルはすべて動作することは確認済み。

```
-- The following OPTIONAL packages have not been found:

 * LibUSB
 * Deflate
 * JBIG
 * LERC
 * liblzma
 * WebP
 * ZLIB
 * PNG
 * JPEG
 * TIFF
 * GIF
 * GLUT
 * SDL
 * Iconv
 * Intl
 * Doxygen
```

## CMakeメモ

- ビルド設定の`set()`は`FetchContent_Declare()`の前に呼ぶ
- `FetchContent_MakeAvailable()`は依存の元になるものから呼ぶ

## Copyright

サンプル音声は以下のURLから取得しました。

[無料 BGM・効果音のフリー音源素材Springin' Sound Stock](https://www.springin.org/sound-stock/category/bgm-short/)