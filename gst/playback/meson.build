playback_sources = [
  'gstdecodebin2.c',
  'gsturidecodebin.c',
  'gstplayback.c',
  'gstplaybackutils.c',
  'gstplaybin2.c',
  'gstplaysink.c',
  'gstplay-enum.c',
  'gstsubtitleoverlay.c',
  'gstplaysinkvideoconvert.c',
  'gstplaysinkaudioconvert.c',
  'gstplaysinkconvertbin.c',
  'gststreamsynchronizer.c'
]

gstplayback = library('gstplayback',
  playback_sources,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args + ['-DCOLORSPACE="videoconvert"'],
  link_with : [ gsttag ],
  dependencies : [audio_dep, video_dep, pbutils_dep, gst_dep, glib_dep],
  install : true,
  install_dir : plugins_install_dir,
)
