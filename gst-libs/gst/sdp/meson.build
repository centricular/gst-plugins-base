gst_sdp_headers = [
  'sdp.h',
  'gstsdp.h',
  'gstmikey.h',
  'gstsdpmessage.h',
]
install_headers(gst_sdp_headers, subdir : 'gstreamer-1.0/gst/sdp/')

gstsdp = library('gstsdp-@0@'.format(api_version),
  'gstsdpmessage.c', 'gstmikey.c',
  include_directories : core_inc,
  c_args : core_args,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [ rtp_dep, gst_dep, gio_dep ],
)
