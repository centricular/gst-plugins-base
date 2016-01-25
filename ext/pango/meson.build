pango_sources = [
  'gstbasetextoverlay.c',
  'gstclockoverlay.c',
  'gsttextoverlay.c',
  'gsttextrender.c',
  'gsttimeoverlay.c',
]

if pango_dep.found()
  gstpango = library('gstpango',
    pango_sources,
    include_directories : core_inc,
    c_args : core_args,
    dependencies : [pango_dep, video_dep, gst_dep, glib_dep],
  )
endif
