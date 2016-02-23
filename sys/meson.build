if x11_dep.found()
  subdir('ximage')
endif

# XXX: Ideally, we want to read the core_conf setting that we set in the main
# meson.build file instead of doing this check twice?
if x11_dep.found() and xvideo_dep.found()
  subdir('xvimage')
endif
