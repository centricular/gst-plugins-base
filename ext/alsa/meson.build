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
    include_directories : core_inc,
    c_args : core_args,
    link_with: [ gsttag ],
    dependencies : [alsa_dep, audio_dep, gst_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
