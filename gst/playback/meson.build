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
  c_args : gst_plugins_base_args + ['-DCOLORSPACE="videoconvert"'],
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [audio_dep, video_dep, pbutils_dep, tag_dep, gst_dep, gst_base_dep],
  install : true,
  install_dir : plugins_install_dir,
)
