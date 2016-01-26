rtsp_sources = [
  'gstrtsptransport.c',
  'gstrtspurl.c',
  'gstrtspmessage.c',
  'gstrtspconnection.c',
  'gstrtspdefs.c',
  'gstrtspextension.c',
  'gstrtsprange.c'
  ]

rtsp_headers = [
  'gstrtspconnection.h',
  'gstrtspdefs.h',
  'gstrtspextension.h',
  'gstrtsp.h',
  'gstrtspmessage.h',
  'gstrtsprange.h',
  'gstrtsptransport.h',
  'gstrtspurl.h',
  'rtsp.h',
]
install_headers(rtsp_headers, subdir : 'gstreamer-1.0/gst/rtsp/')

mkenums = find_program('rtsp_mkenum.py')

gstrtsp_h = custom_target('gstrtspenum_h',
  output : 'gstrtsp-enumtypes.h',
  input : rtsp_headers,
  install : true,
  install_dir : 'include/gstreamer-1.0/gst/rtsp/',
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstrtsp_c = custom_target('gstrtspenum_c',
  output : 'gstrtsp-enumtypes.c',
  input : rtsp_headers,
  command : [mkenums, '@OUTPUT@', '@INPUT@'])


gst_rtsp = library('gstrtsp-@0@'.format(api_version),
  rtsp_sources,
  gstrtsp_h, gstrtsp_c,
  include_directories : core_inc,
  c_args : core_args,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [ gst_dep, gio_dep ],
)
rtsp_dep = declare_dependency(link_with : gst_rtsp, sources : [ gstrtsp_h ])
