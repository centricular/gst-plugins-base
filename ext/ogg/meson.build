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
    include_directories : core_inc,
    c_args : core_args,
    link_with: [ gsttag, gstriff ],
    dependencies : [ ogg_dep, audio_dep, pbutils_dep, gst_dep, glib_dep ],
  )
endif
