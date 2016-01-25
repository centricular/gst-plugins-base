rtsp_sources = [
  'gstrtsptransport.c',
  'gstrtspurl.c',
  'gstrtspmessage.c',
  'gstrtspconnection.c',
  'gstrtspdefs.c',
  'gstrtspextension.c',
  'gstrtsprange.c'
  ]

mkenums = find_program('rtsp_mkenum.py')

gstrtsp_h = custom_target('gstrtspenum_h',
  output : 'gstrtsp-enumtypes.h',
  input : 'gstrtspdefs.h',
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstrtsp_c = custom_target('gstrtspenum_c',
  output : 'gstrtsp-enumtypes.c',
  input : 'gstrtspdefs.h',
  command : [mkenums, '@OUTPUT@', '@INPUT@'])


gstsdp = library('gstrtsp',
  rtsp_sources,
  gstrtsp_h, gstrtsp_c,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [gst_dep, glib_dep],
)
