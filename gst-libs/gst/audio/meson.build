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
  'gstaudiopack-dist.h',
  'gstaudioringbuffer.h',
  'gstaudiosink.h',
  'gstaudiosrc.h',
  'streamvolume.h',
]

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
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstaudio_c = custom_target('gstaudioenum_c',
  output : 'audio-enumtypes.c',
  input : audio_mkenum_headers,
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

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
  include_directories : core_inc,
  c_args: core_args,
  dependencies : [gst_dep, gst_base_dep, glib_dep])

audio_dep = declare_dependency(link_with : gstaudio,
  sources : [gstaudio_h]
)