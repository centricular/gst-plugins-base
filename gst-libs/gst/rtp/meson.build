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
  'gstrtphdrext.h',
  'gstrtppayloads.h',
  'rtp.h',
]
install_headers(rtp_headers, subdir : 'gstreamer-1.0/gst/rtp/')

mkenums = find_program('rtp_mkenum.py')

gstrtp_enum_h = custom_target('gstrtp_enum_h',
  output : 'gstrtp-enumtypes.h',
  input : rtp_headers,
  install : true,
  install_dir : 'include/gstreamer-1.0/gst/rtp/',
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstrtp_enum_c = custom_target('gstrtp_enum_c',
  output : 'gstrtp-enumtypes.c',
  input : rtp_headers,
  depends : [gstaudio_h, gstrtp_enum_h],
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gst_rtp = library('gstrtp-@0@'.format(api_version),
  rtp_sources, gstrtp_enum_c, gstrtp_enum_h,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [audio_dep, gst_dep, gst_base_dep, glib_dep],
  # Only used with MSVC
  module_defs_file: meson.source_root() + '/win32/common/libgstrtp.def',
)
rtp_dep = declare_dependency(link_with : gst_rtp, sources : [ gstrtp_enum_h ])
