project('vivo_fastboot', 'c', 'cpp',
    version : '1.0',
    meson_version : '>= 0.50.0',
    default_options : [ 'warning_level=3', 'buildtype=debugoptimized', 'cpp_std=c++11' ]
)

zlib_dep = dependency('zlib')
pcre_dep = dependency('libpcre')
selinux_dep = dependency('libselinux')

external_includes = [
	include_directories('./external/ext4_utils/include/ext4_utils'),
	include_directories('./external/ext4_utils/include'),
	include_directories('./external/mkbootimg'),
	include_directories('./external/libsparse/include'),
	include_directories('./external/libzipfile/include'),
	include_directories('./external'),
	include_directories('./external/libutils/include'),
	include_directories('./external/libcutils/include'),
]

libsparse = static_library('libsparse',
	[
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
	],
	include_directories: external_includes,
)

libzipfile = static_library('libzipfile',
	[
		'./external/libzipfile/zipfile.c',
		'./external/libzipfile/centraldir.c',
	],
	include_directories: external_includes,
)

libstringprintf = static_library('libstringprintf',
	'./external/android-base/stringprintf.cpp',
	include_directories: external_includes,
)

libext4_utils = static_library('libext4_utils',
	[
		'./external/ext4_utils/make_ext4fs.c',
		'./external/ext4_utils/ext4_utils.c',
		'./external/ext4_utils/contents.c',
		'./external/ext4_utils/allocate.c',
		'./external/ext4_utils/wipe.c',
		'./external/ext4_utils/sha1.c',
		'./external/ext4_utils/ext4_sb.c',
		'./external/ext4_utils/indirect.c',
		'./external/ext4_utils/extent.c',
		'./external/ext4_utils/crc16.c',
	],
	dependencies: [selinux_dep],
	include_directories: external_includes,
	link_with: []
)


executable('vivo_fastboot',
	[
		'bootimg.c',
		'engine.c',
		'fastboot.c',
		'protocol.c',
		'usb_linux.c',
		'util_linux.c'
	],
	dependencies: [zlib_dep],
	include_directories: external_includes,
	link_with: [libsparse, libzipfile, libstringprintf, libext4_utils]
)
