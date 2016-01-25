aconv_sources = [
  'gstaudioconvert.c',
  'plugin.c'
  ]

gstaudioconvert = library('gstaudioconvert',
  aconv_sources,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [audio_dep, gst_dep, glib_dep],
  install : true,
  install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
)
