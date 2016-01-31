audiotest = library('gstaudiotestsrc',
  'gstaudiotestsrc.c', gstaudio_h,
  include_directories : gst_plugins_base_incs,
  c_args: gst_plugins_base_args,
  dependencies : [audio_dep, gst_dep, gst_base_dep, glib_dep],
  install : true,
  install_dir : plugins_install_dir,
)
