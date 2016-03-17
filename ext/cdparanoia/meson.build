cdparanoia_deps = []
cdparanoia_found = false

# cdparanoia upstream has a pkg-config file only in post-10.2 SVN so far, no release yet
cdparanoia_dep = dependency('cdparanoia-3', version : '>=10.2', required : false)
if cdparanoia_dep.found()
  cdparanoia_deps = [cdparanoia_dep]
  cdparanoia_found = true
else
  cdparanoia_dep = cc.find_library('cdda_paranoia', required : false)
  cdinterface_dep = cc.find_library('cdda_interface', required : false)
  if cdparanoia_dep.found() and cdinterface_dep.found()
    cdparanoia_deps = [cdparanoia_dep, cdinterface_dep]
    cdparanoia_found = true
    if cc.has_function('cdda_open', prefix : '#include <cdda/cdda_interface.h>')
      core_conf.set('CDPARANOIA_HEADERS_IN_DIR', true)
    elif cc.has_function('cdda_open', prefix : '#include <cdda_interface.h>')
      core_conf.set('CDPARANOIA_HEADERS_IN_DIR', false)
    endif
  endif
endif

if cdparanoia_found
  gstcdparanoia = library('gstcdparanoia',
    ['gstcdparanoiasrc.c'],
    include_directories : gst_plugins_base_incs,
    c_args : gst_plugins_base_args,
    dependencies : cdparanoia_deps + [audio_dep, gst_dep, glib_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
