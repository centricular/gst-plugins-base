gio_sources = ['gstgio.c',
  'gstgiobasesink.c',
  'gstgiobasesrc.c',
  'gstgiosink.c',
  'gstgiosrc.c',
  'gstgiostreamsink.c',
  'gstgiostreamsrc.c',
]

gstgio = library('gstgio',
  gio_sources,
  c_args : gst_plugins_base_args,
  include_directories : gst_plugins_base_incs,
  dependencies : [ gst_base_dep, gst_dep, gio_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
