adder = library('gstapp',
  'gstapp.c',
  include_directories : gst_plugins_base_incs,
  c_args: gst_plugins_base_args,
  link_with : gstapp,
  dependencies : [ gst_base_dep, gst_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
