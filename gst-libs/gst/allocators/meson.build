gst_allocators_headers = [
  'allocators.h',
  'gstfdmemory.h',
  'gstdmabuf.h',
]
install_headers(gst_allocators_headers, subdir : 'gstreamer-1.0/gst/allocators/')

gstallocators = library('gstallocators-@0@'.format(api_version),
  [ 'gstdmabuf.c', 'gstfdmemory.c' ],
  c_args : gst_plugins_base_args,
  include_directories : gst_plugins_base_incs,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [gst_dep, glib_dep],
  vs_module_defs: vs_module_defs_dir + 'libgstallocators.def',
)
# TODO: generate gir

allocators_dep = declare_dependency(link_with: gstallocators)
