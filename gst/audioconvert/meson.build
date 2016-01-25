aconv_sources = [
  'gstaudioconvert.c',
  'plugin.c'
  ]

gstaudioconvert = library('gstaudioconvert',
  aconv_sources,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [audio_dep, gst_dep, glib_dep],
)
