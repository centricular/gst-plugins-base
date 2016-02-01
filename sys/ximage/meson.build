gstximage = library('gstximagesink',
  'ximagesink.c', 'ximage.c', 'ximagepool.c',
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [ video_dep, gst_base_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
