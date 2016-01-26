theora_sources = [
  'gsttheora.c',
  'gsttheoraparse.c',
]

theora_deps = [ ]

if theoradec_dep.found() or theoraenc_dep.found()
  if theoradec_dep.found()
    theora_sources += [ 'gsttheoradec.c' ]
    theora_deps += theoradec_dep
  endif
  if theoraenc_dep.found()
    theora_sources += [ 'gsttheoraenc.c' ]
    theora_deps += theoraenc_dep
  endif
  gsttheora = library('gsttheora',
    theora_sources,
    include_directories : core_inc,
    c_args : core_args,
    link_with: [ gsttag ],
    dependencies : theora_deps + [ video_dep, gst_dep, glib_dep ],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
