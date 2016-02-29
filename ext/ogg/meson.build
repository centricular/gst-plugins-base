ogg_sources = [
  'dirac_parse.c',
  'gstoggaviparse.c',
  'gstogg.c',
  'gstoggdemux.c',
  'gstoggmux.c',
  'gstoggparse.c',
  'gstoggstream.c',
  'gstogmparse.c',
  'vorbis_parse.c',
]

if ogg_dep.found()
  gstogg = library('gstogg',
    ogg_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    link_with: [gsttag, gstriff],
    dependencies : [ogg_dep, audio_dep, pbutils_dep, gst_dep, gst_base_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
