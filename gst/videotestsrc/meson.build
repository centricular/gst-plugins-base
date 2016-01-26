videotestsrc_orc_h = configure_file(input : 'gstvideotestsrcorc-dist.h',
  output : 'gstvideotestsrcorc.h',
  configuration : configuration_data())

videotestsrc_orc_c = configure_file(input : 'gstvideotestsrcorc-dist.c',
  output : 'gstvideotestsrcorc.c',
  configuration : configuration_data())

gstvideotestsrc = library('gstvideotestsrc',
  'gstvideotestsrc.c', 'videotestsrc.c', videotestsrc_orc_c, videotestsrc_orc_h,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [video_dep, gst_dep, glib_dep],
  install : true,
  install_dir : plugins_install_dir,
)
