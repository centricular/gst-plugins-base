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

gstriff = library('gstriff',
  riff_sources,
  c_args : core_args,
  include_directories : core_inc,
  version : libversion,
  soversion : soversion,
  install : true,
 dependencies : [audio_dep, gst_dep, glib_dep],
)
