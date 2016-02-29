xvimage_sources = [
  'xvcontext.c',
  'xvimage.c',
  'xvimageallocator.c',
  'xvimagepool.c',
  'xvimagesink.c',
]

gstxvimage = library('gstxvimage',
  xvimage_sources,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [video_dep, gst_base_dep, gst_dep, glib_dep, x11_dep, xshm_dep, xvideo_dep, libm],
  install : true,
  install_dir : plugins_install_dir,
)
