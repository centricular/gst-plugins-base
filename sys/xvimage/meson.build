xvimage_sources = [
  'xvimagesink.c',
  'xvimage.c',
  'xvimagepool.c',
  'xvimageallocator.c',
]

gstxvimage = library('gstxvimage',
  xvimage_sources,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [ video_dep, gst_base_dep ],
  install : true,
  install_dir : plugins_install_dir,
)
