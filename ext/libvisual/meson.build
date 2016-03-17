libvisual_sources = [
  'visual.c',
  'plugin.c',
]

libvisual_dep = dependency('libvisual-0.4', version : '>= 0.4.0', required : false)
if libvisual_dep.found()
  runcmd = run_command('pkg-config', '--variable=pluginsbasedir', 'libvisual-0.4')
  if runcmd.returncode() == 0
    core_conf.set('LIBVISUAL_PLUGINSBASEDIR', '"@0@"'.format(runcmd.stdout().strip()))
  endif
endif

if libvisual_dep.found()
  gstlibvisual = library('gstlibvisual',
    libvisual_sources,
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    dependencies : [ libvisual_dep, audio_dep, video_dep, pbutils_dep, gst_dep, glib_dep ],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
