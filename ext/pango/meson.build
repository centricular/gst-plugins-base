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
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    dependencies : [pango_dep, video_dep, gst_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
