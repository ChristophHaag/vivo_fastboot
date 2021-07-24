project('vivo_fastboot', 'cpp',
    version : '1.0',
    meson_version : '>= 0.50.0',
    default_options : [ 'warning_level=3', 'buildtype=debugoptimized', 'cpp_std=c++11' ]
)

sources = [
	'bootimg.c',
	'engine.c',
	'fastboot.c',
	'protocol.c',
	'usbtest.c',
	'usb_linux.c',
	'util_linux.c',
	#'usb_osx.c',
	#'util_osx.c',
	#'usb_windows.c',
	#'util_windows.c',
]

libsparse_sources = [
	'./external/libsparse/append2simg.c',
	'./external/libsparse/backed_block.c',
	'./external/libsparse/img2simg.c',
	'./external/libsparse/output_file.c',
	'./external/libsparse/simg2img.c',
	'./external/libsparse/simg2img.c',
	'./external/libsparse/sparse.c',
	'./external/libsparse/sparse_crc32.c',
	'./external/libsparse/sparse_err.c',
	'./external/libsparse/sparse_read.cpp',
]

external_includes = [
	include_directories('./external/ext4_utils/include/ext4_utils'),
	include_directories('./external/mkbootimg'),
	include_directories('./external/libsparse/include'),
	include_directories('./external/libzipfile/include'),
	include_directories('./external'),
	#include_directories('./external/ext4_utils'),
]


executable('vivo_fastboot',
	sources + libsparse_sources,
	include_directories: external_includes,
)
