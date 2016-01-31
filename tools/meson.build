tool_deps = [pbutils_dep, audio_dep, video_dep, gst_dep]

executable('gst-device-monitor-@0@'.format(api_version),
  'gst-device-monitor.c',
  link_with : gsttag,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : tool_deps,
)

executable('gst-discoverer-@0@'.format(api_version),
  'gst-discoverer.c',
  link_with : gsttag,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : tool_deps,
)

executable('gst-play-@0@'.format(api_version),
  'gst-play.c', 'gst-play-kb.c',
  link_with : gsttag,
  include_directories : gst_plugins_base_incs,
  c_args : gst_plugins_base_args,
  dependencies : [ tool_deps, libm ],
)
