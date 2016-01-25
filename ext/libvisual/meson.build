libvisual_sources = [
  'visual.c',
  'plugin.c',
]

if libvisual_dep.found()
  gstlibvisual = library('gstlibvisual',
    libvisual_sources,
    include_directories : core_inc,
    c_args : core_args,
    dependencies : [ libvisual_dep, video_dep, pbutils_dep, gst_dep, glib_dep ],
    install : true,
    install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
  )
endif
