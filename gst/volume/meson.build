volume_orc_h = configure_file(input : 'gstvolumeorc-dist.h',
  output : 'gstvolumeorc.h',
  configuration : configuration_data())

volume_orc_c = configure_file(input : 'gstvolumeorc-dist.c',
  output : 'gstvolumeorc.c',
  configuration : configuration_data())

gstvolume = library('gstvolume', 'gstvolume.c', volume_orc_c, volume_orc_h,
  c_args : gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [audio_dep, gst_dep, gst_base_dep],
  install : true,
  install_dir : plugins_install_dir,
)
