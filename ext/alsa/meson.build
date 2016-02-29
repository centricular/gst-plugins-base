alsa_sources = [
  'gstalsa.c',
  'gstalsadeviceprobe.c',
  'gstalsamidisrc.c',
  'gstalsaplugin.c',
  'gstalsasink.c',
  'gstalsasrc.c',
]

if alsa_dep.found()
  gstalsa = library('gstalsa',
    alsa_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    link_with: [gsttag],
    dependencies : [alsa_dep, audio_dep, gst_dep, gst_base_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
