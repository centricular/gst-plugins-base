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
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [ giounix_dep, gst_base_dep, gst_net_dep, gst_dep, glib_dep ],
  install : true,
  install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
)
