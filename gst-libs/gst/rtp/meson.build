rtp_sources = [
  'gstrtpbuffer.c',
  'gstrtcpbuffer.c',
  'gstrtppayloads.c',
  'gstrtphdrext.c',
  'gstrtpbaseaudiopayload.c',
  'gstrtpbasepayload.c',
  'gstrtpbasedepayload.c'
  ]

rtp_headers = [
  'gstrtcpbuffer.h',
  'gstrtpbaseaudiopayload.h',
  'gstrtpbasedepayload.h',
  'gstrtpbasepayload.h',
  'gstrtpbuffer.h',
  'gstrtpdefs.h',
  'gstrtp-enumtypes.h',
  'gstrtphdrext.h',
  'gstrtppayloads.h',
  'rtp.h',
]
install_headers(rtp_headers, subdir : 'gstreamer-1.0/gst/rtp/')

gst_rtp = library('gstrtp',
  rtp_sources,
  include_directories : core_inc,
  c_args : core_args,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [gst_dep, glib_dep]
)
