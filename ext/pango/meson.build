pango_sources = [
  'gstbasetextoverlay.c',
  'gstclockoverlay.c',
  'gsttextoverlay.c',
  'gsttextrender.c',
  'gsttimeoverlay.c',
]

pango_dep = dependency('pangocairo', version : '>=1.22.0', required : false)

if pango_dep.found()
  gstpango = library('gstpango',
    pango_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    dependencies : [pango_dep, video_dep, gst_dep, glib_dep, libm],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
