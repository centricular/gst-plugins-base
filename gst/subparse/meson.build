subparse_sources = [
  'gstssaparse.c',
  'gstsubparse.c',
  'samiparse.c',
  'tmplayerparse.c',
  'mpl2parse.c',
  'qttextparse.c',
]

gstsubparse = library('gstsubparse',
  subparse_sources,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [ gst_base_dep, gst_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
