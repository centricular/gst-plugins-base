if cdparanoia_dep.found()
  gstcdparanoia = library('gstcdparanoia',
    [ 'gstcdparanoiasrc.c' ],
    include_directories : core_inc,
    c_args : core_args,
    dependencies : [cdparanoia_dep, audio_dep, gst_dep, glib_dep],
    install : true,
    install_dir : '@0@/gstreamer-1.0'.format(get_option('libdir')),
  )
endif
