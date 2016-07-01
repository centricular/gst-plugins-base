audio_src= [
  'audio.c',
  'audio-channel-mixer.c',
  'audio-channels.c',
  'audio-converter.c',
  'audio-format.c',
  'audio-info.c',
  'audio-quantize.c',
  'gstaudiobasesink.c',
  'gstaudiobasesrc.c',
  'gstaudiocdsrc.c',
  'gstaudioclock.c',
  'gstaudiodecoder.c',
  'gstaudioencoder.c',
  'gstaudiofilter.c',
  'gstaudioiec61937.c',
  'gstaudiometa.c',
  'gstaudioringbuffer.c',
  'gstaudiosink.c',
  'gstaudiosrc.c',
  'gstaudioutilsprivate.c',
  'streamvolume.c',
]

# FIXME: check headers
audio_headers = [
  'audio-channel-mixer.h',
  'audio-channels.h',
  'audio-converter.h',
  'audio-format.h',
  'audio.h',
  'audio-info.h',
  'audio-quantize.h',
  'gstaudiobasesink.h',
  'gstaudiobasesrc.h',
  'gstaudiocdsrc.h',
  'gstaudioclock.h',
  'gstaudiodecoder.h',
  'gstaudioencoder.h',
  'gstaudiofilter.h',
  'gstaudioiec61937.h',
  'gstaudiometa.h',
  'gstaudioringbuffer.h',
  'gstaudiosink.h',
  'gstaudiosrc.h',
  'streamvolume.h',
]
install_headers(audio_headers, subdir : 'gstreamer-1.0/gst/audio/')

audio_mkenum_headers = [
  'audio.h',
  'audio-format.h',
  'audio-channels.h',
  'audio-channel-mixer.h',
  'audio-converter.h',
  'audio-info.h',
  'audio-quantize.h',
  'gstaudioringbuffer.h',
]

mkenums = find_program('audio_mkenum.py')
gstaudio_h = custom_target('gstaudioenum_h',
  output : 'audio-enumtypes.h',
  input : audio_mkenum_headers,
  install : true,
  install_dir : 'include/gstreamer-1.0/gst/audio/',
  command : [mkenums, perl, glib_mkenums, '@OUTPUT@', '@INPUT@'])

gstaudio_c = custom_target('gstaudioenum_c',
  output : 'audio-enumtypes.c',
  input : audio_mkenum_headers,
  depends : [gstaudio_h],
  command : [mkenums, perl, glib_mkenums, '@OUTPUT@', '@INPUT@'])

# FIXME: use orc to generate these if available!
cdata = configuration_data()
configure_file(input : 'gstaudiopack-dist.h',
  output : 'gstaudiopack.h',
  configuration : cdata)

audio_orc_c = configure_file(input : 'gstaudiopack-dist.c',
  output : 'gstaudiopack.c',
  configuration : cdata)

gstaudio = library('gstaudio-@0@'.format(api_version),
  audio_src, gstaudio_h, gstaudio_c, audio_orc_c,
  c_args: gst_plugins_base_args,
  include_directories: [configinc, libsinc],
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : glib_deps + [tag_dep, gst_dep, gst_base_dep, libm],
  vs_module_defs: vs_module_defs_dir + 'libgstaudio.def',
)
# TODO: generate gir

audio_dep = declare_dependency(link_with : gstaudio,
  include_directories : [libsinc],
  sources : [gstaudio_h]
)
