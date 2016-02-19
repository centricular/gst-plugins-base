adder_orc_h = configure_file(input : 'gstadderorc-dist.h',
  output : 'gstadderorc.h',
  configuration : configuration_data())

adder_orc_c = configure_file(input : 'gstadderorc-dist.c',
  output : 'gstadderorc.c',
  configuration : configuration_data())

adder = library('gstadder',
  'gstadder.c', adder_orc_c, adder_orc_h,
  include_directories : core_inc,
  c_args: core_args,
  dependencies : [audio_dep, gst_dep, gst_base_dep, glib_dep],
  install : true,
  install_dir : plugins_install_dir,
)
