adder_orc_h = configure_file(input : 'gstadderorc-dist.h',
  output : 'gstadderorc.h',
  configuration : configuration_data())

adder_orc_c = configure_file(input : 'gstadderorc-dist.c',
  output : 'gstadderorc.c',
  configuration : configuration_data())

adder = library('gstadder',
  'gstadder.c', adder_orc_c, adder_orc_h,
  c_args: gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [audio_dep, gst_dep, gst_base_dep],
  install : true,
  install_dir : plugins_install_dir,
)
