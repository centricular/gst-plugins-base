volume_orc_h = configure_file(input : 'gstvolumeorc-dist.h',
  output : 'gstvolumeorc.h',
  configuration : configuration_data())

volume_orc_c = configure_file(input : 'gstvolumeorc-dist.c',
  output : 'gstvolumeorc.c',
  configuration : configuration_data())

gstvolume = library('gstvolume', 'gstvolume.c', volume_orc_c, volume_orc_h,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [audio_dep, gst_dep, glib_dep]
)
