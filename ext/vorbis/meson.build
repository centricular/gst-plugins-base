vorbis_sources = [
  'gstvorbis.c',
  'gstvorbisdec.c',
  'gstvorbisdeclib.c',
  'gstvorbisenc.c',
  'gstvorbisparse.c',
  'gstvorbistag.c',
  'gstvorbiscommon.c',
]

vorbisidec_sources = [
  'gstivorbisdec.c',
  'gstvorbisdec.c',
  'gstvorbisdeclib.c',
  'gstvorbiscommon.c',
]

if vorbis_dep.found()
  vorbis_deps = [ vorbis_dep ]
  if vorbisenc_dep.found()
    vorbis_deps += vorbisenc_dep
  endif
  gstvorbis = library('gstvorbis',
    vorbis_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    link_with: [ gsttag ],
    dependencies : vorbis_deps + [ audio_dep, gst_dep, glib_dep ],
    install : true,
    install_dir : plugins_install_dir,
  )
endif

if vorbisidec_dep.found()
  gstivorbisdec = library('gstivorbisdec',
    vorbisidec_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    link_with: [ gsttag ],
    dependencies : [ vorbisidec_dep, audio_dep, gst_dep, glib_dep ],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
