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
  c_args : core_args,
  include_directories : core_inc,
  dependencies : [ gst_base_dep, gst_dep, giounix_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
