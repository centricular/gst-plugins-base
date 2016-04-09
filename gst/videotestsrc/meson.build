videotestsrc_orc_h = configure_file(input : 'gstvideotestsrcorc-dist.h',
  output : 'gstvideotestsrcorc.h',
  configuration : configuration_data())

videotestsrc_orc_c = configure_file(input : 'gstvideotestsrcorc-dist.c',
  output : 'gstvideotestsrcorc.c',
  configuration : configuration_data())

gstvideotestsrc = library('gstvideotestsrc',
  'gstvideotestsrc.c', 'videotestsrc.c', videotestsrc_orc_c, videotestsrc_orc_h,
  c_args : gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [video_dep, gst_dep, gst_base_dep, libm],
  install : true,
  install_dir : plugins_install_dir,
)
