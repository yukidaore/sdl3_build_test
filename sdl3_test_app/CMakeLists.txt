cmake_minimum_required(VERSION 3.16)
project(sdl3_test_app)

# SDL3一括ビルドの参照
add_subdirectory("../sdl3_cmake_all" "${CMAKE_CURRENT_BINARY_DIR}/sdl3_deps")

# ------------------------------------------------------------------------------
# サンプルアプリ1: SDL_imageサンプル showimage
# ------------------------------------------------------------------------------
add_executable(sdl3_test_image showimage.c)

# リンク設定
target_link_libraries(sdl3_test_image PRIVATE SDL3::SDL3)
target_link_libraries(sdl3_test_image PRIVATE SDL3_image::SDL3_image)

if(WIN32)
	# 実行ファイルの依存DLLをビルド完了後に実行ファイルの出力ディレクトリへコピー
	add_custom_command(TARGET sdl3_test_image POST_BUILD
		COMMAND ${CMAKE_COMMAND} -E copy_if_different
		$<TARGET_RUNTIME_DLLS:sdl3_test_image>
		$<TARGET_FILE_DIR:sdl3_test_image>
		COMMAND_EXPAND_LISTS
	)
endif()

# ------------------------------------------------------------------------------
# サンプルアプリ1: SDL_mixerサンプル testmixer
# ------------------------------------------------------------------------------
add_executable(sdl3_test_mixer testmixer.c)

# リンク設定
target_link_libraries(sdl3_test_mixer PRIVATE SDL3::SDL3)
target_link_libraries(sdl3_test_mixer PRIVATE SDL3_mixer::SDL3_mixer)

if(WIN32)
	# 実行ファイルの依存DLLをビルド完了後に実行ファイルの出力ディレクトリへコピー
	add_custom_command(TARGET sdl3_test_mixer POST_BUILD
		COMMAND ${CMAKE_COMMAND} -E copy_if_different
		$<TARGET_RUNTIME_DLLS:sdl3_test_mixer>
		$<TARGET_FILE_DIR:sdl3_test_mixer>
		COMMAND_EXPAND_LISTS
	)
endif()

# ------------------------------------------------------------------------------
# サンプルアプリ1: SDL_netサンプル simple-http-get
# ------------------------------------------------------------------------------
add_executable(sdl3_test_net simple-http-get.c)

# リンク設定
target_link_libraries(sdl3_test_net PRIVATE SDL3::SDL3)
target_link_libraries(sdl3_test_net PRIVATE SDL3_net::SDL3_net)

if(WIN32)
	# 実行ファイルの依存DLLをビルド完了後に実行ファイルの出力ディレクトリへコピー
	add_custom_command(TARGET sdl3_test_net POST_BUILD
		COMMAND ${CMAKE_COMMAND} -E copy_if_different
		$<TARGET_RUNTIME_DLLS:sdl3_test_net>
		$<TARGET_FILE_DIR:sdl3_test_net>
		COMMAND_EXPAND_LISTS
	)
endif()