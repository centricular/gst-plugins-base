tag_sources = [
  'gstvorbistag.c',
  'gstid3tag.c',
  'gstxmptag.c',
  'gstexiftag.c',
  'lang.c',
  'licenses.c',
  'tags.c',
  'gsttagdemux.c',
  'gsttagmux.c',
  'gsttageditingprivate.c',
  'id3v2.c',
  'id3v2frames.c',
  'xmpwriter.c',
]

tag_headers = [
  'gsttagdemux.h',
  'gsttagmux.h',
  'tag.h',
  'xmpwriter.h',
]
install_headers(tag_headers, subdir : 'gstreamer-1.0/gst/tag/')

gsttag = library('gsttag-@0@'.format(api_version),
  tag_sources,
  c_args : core_args,
  include_directories: core_inc,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [gst_base_dep, gst_dep, glib_dep])

# FIXME: iso-codes stuff
# little program that reads iso_639.xml and outputs tables for us as fallback
# for when iso-codes are not available (and so we don't have to read the xml
# just to map codes)
#executable('mklangtables', 'mklangtables.c',
#  dependencies : gst_dep,
#  install : false,
#)
executable('mklicensestables', 'mklicensestables.c',
  include_directories : core_inc,
  c_args : core_args,
  link_with : gsttag,
  dependencies : gst_dep,
  install : false,
)