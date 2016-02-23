riff_sources = [
  'riff.c',
  'riff-media.c',
  'riff-read.c',
]

riff_headers = [
  'riff.h',
  'riff-ids.h',
  'riff-media.h',
  'riff-read.h',
]
install_headers(riff_headers, subdir : 'gstreamer-1.0/gst/riff/')

gstriff = library('gstriff-@0@'.format(api_version),
  riff_sources,
  c_args : gst_plugins_base_args,
  include_directories : gst_plugins_base_incs,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [audio_dep, gst_dep, glib_dep],
  # Only used with MSVC
  module_defs_file: meson.source_root() + '/win32/common/libgstriff.def',
)

riff_dep = declare_dependency(link_with: gstriff)
