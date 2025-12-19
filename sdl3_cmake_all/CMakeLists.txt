cmake_minimum_required(VERSION 3.16)
project(sdl3-cmake-all)

include(FetchContent)

# ------------------------------------------------------------------------------
# 全体コンパイル設定(warn潰し)
# ------------------------------------------------------------------------------
if(MSVC)
	# SDL_imageのexternalのビルドでコードページとcrt secure関連のwarnが出るのを抑止
	add_compile_options("$<$<COMPILE_LANGUAGE:C,CXX>:/wd4819>")
	add_compile_definitions("$<$<COMPILE_LANGUAGE:C,CXX>:_CRT_SECURE_NO_WARNINGS>")
endif()

# ------------------------------------------------------------------------------
# SDL3本体
# ------------------------------------------------------------------------------
# ビルド設定
set(SDL_SHARED ON CACHE BOOL "Build shared SDL library")
set(SDL_STATIC OFF CACHE BOOL "Build static SDL library")
set(SDL_TEST_LIBRARY OFF CACHE BOOL "Build SDL test library")

FetchContent_Declare(
	SDL3
	GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
	GIT_TAG main
)

# ------------------------------------------------------------------------------
# SDL3_image
# ------------------------------------------------------------------------------
# ビルド設定
# set(SDLIMAGE_VENDORED ON CACHE BOOL "Use bundled dependencies for SDL_image")
# set(SDLIMAGE_SAMPLES OFF CACHE BOOL "Disable SDL_image samples")

FetchContent_Declare(
	SDL3_image
	GIT_REPOSITORY https://github.com/libsdl-org/SDL_image.git
	GIT_TAG main
)

# ------------------------------------------------------------------------------
# SDL3_mixer
# ------------------------------------------------------------------------------
# ビルド設定

FetchContent_Declare(
	SDL3_mixer
	GIT_REPOSITORY https://github.com/libsdl-org/SDL_mixer.git
	GIT_TAG main
)

# ------------------------------------------------------------------------------
# SDL3_mixer
# ------------------------------------------------------------------------------
# ビルド設定

FetchContent_Declare(
	SDL3_net
	GIT_REPOSITORY https://github.com/libsdl-org/SDL_net.git
	GIT_TAG main
)

# ------------------------------------------------------------------------------
# ビルドツリー
# ------------------------------------------------------------------------------
FetchContent_MakeAvailable(SDL3)
FetchContent_MakeAvailable(SDL3_image)
FetchContent_MakeAvailable(SDL3_mixer)
FetchContent_MakeAvailable(SDL3_net)
