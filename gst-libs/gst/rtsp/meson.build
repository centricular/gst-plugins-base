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

# FIXME: This should use find_library once it's fixed on Windows
if host_machine.system() == 'windows'
  if cc.get_id() == 'msvc'
    win32_libs = ['ws2_32.lib']
  else
    win32_libs = ['-lws2_32']
  endif
else
  win32_libs = []
endif

gst_rtsp = library('gstrtsp-@0@'.format(api_version),
  rtsp_sources,
  gstrtsp_h, gstrtsp_c,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  version : libversion,
  soversion : soversion,
  install : true,
  link_args : win32_libs,
  dependencies : [ gst_dep, gio_dep ],
  # Only used with MSVC
  module_defs_file: meson.source_root() + '/win32/common/libgstrtsp.def',
)
rtsp_dep = declare_dependency(link_with : gst_rtsp, sources : [ gstrtsp_h ])
