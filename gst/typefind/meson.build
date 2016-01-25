gsttypefind = library('gsttypefindfunctions',
  'gsttypefindfunctions.c',
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [ pbutils_dep, gst_dep, giounix_dep ],
  install : true,
  install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
)
