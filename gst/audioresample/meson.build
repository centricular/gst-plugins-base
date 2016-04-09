resample_sources = ['gstaudioresample.c',
  'speex_resampler_int.c',
  'speex_resampler_float.c',
  'speex_resampler_double.c'
]

audioresample = library('gstaudioresample',
  resample_sources,
  c_args : gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  dependencies : glib_deps + [audio_dep, gst_dep, gst_base_dep, libm],
  install : true,
  install_dir : plugins_install_dir,
)
