gstvideorate = library('gstvideorate',
  'gstvideorate.c',
  c_args : gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [video_dep, gst_base_dep, gst_dep],
  install : true,
  install_dir : plugins_install_dir,
)
