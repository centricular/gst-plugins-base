if cdparanoia_dep.found()
  gstcdparanoia = library('gstcdparanoia',
    [ 'gstcdparanoiasrc.c' ],
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    dependencies : [cdparanoia_dep, audio_dep, gst_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
