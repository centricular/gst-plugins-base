gstximage = library('gstximagesink',
  'ximagesink.c', 'ximage.c', 'ximagepool.c',
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [gst_dep, glib_dep],
  install : true,
  install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
)
