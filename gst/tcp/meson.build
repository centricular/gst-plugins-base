tcp_sources = [
  'gstmultihandlesink.c',
  'gstmultisocketsink.c',
  'gstsocketsrc.c',
  'gsttcpclientsrc.c',
  'gsttcpclientsink.c',
  'gsttcpserversrc.c',
  'gsttcpserversink.c',
  'gsttcpplugin.c',
]

if core_conf.has('HAVE_SYS_SOCKET_H')
   tcp_sources += 'gstmultifdsink.c'
endif

gsttcp = library('gsttcp',
  tcp_sources,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [ gst_base_dep, gst_net_dep, gst_dep, glib_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
