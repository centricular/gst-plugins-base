videoscale_sources = [
  'gstvideoscale.c',
]

gstvideoscale = library('gstvideoscale',
  videoscale_sources,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [video_dep, gst_dep, glib_dep]
)
