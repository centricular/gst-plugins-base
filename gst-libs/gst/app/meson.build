app_sources = ['gstappsrc.c', 'gstappsink.c']

app_headers = [ 'app.h', 'gstappsrc.h', 'gstappsink.h' ]
install_headers(app_headers, subdir : 'gstreamer-1.0/gst/app/')

genmarshal = find_program('app_marshal.py')

marshal_header = custom_target('app_marshal_h',
  output : 'gstapp-marshal.h',
  input : 'gstapp-marshal.list',
  command : [genmarshal, '@INPUT@', '@OUTPUT@']
)
marshal_src = custom_target('app_marshal_c',
  output : 'gstapp-marshal.c',
  input : 'gstapp-marshal.list',
  command : [genmarshal, '@INPUT@', '@OUTPUT@']
)


gstapp = library('gstapp-@0@'.format(api_version),
  app_sources, marshal_src, marshal_header,
  c_args : core_args,
  include_directories : core_inc,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [ gst_base_dep ],
  )
