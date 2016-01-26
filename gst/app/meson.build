adder = library('gstapp',
  'gstapp.c',
  include_directories : core_inc,
  c_args: core_args,
  link_with : gstapp,
  dependencies : [ gst_base_dep, gst_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
