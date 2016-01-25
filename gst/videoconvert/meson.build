vconvert_sources = [
  'gstvideoconvert.c',
]

gstvideoconvert = library('gstvideoconvert',
  vconvert_sources,
  include_directories : core_inc,
  c_args : core_args,
  dependencies : [video_dep, gst_dep, glib_dep]
)
