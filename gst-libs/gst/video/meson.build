video_sources = [
  'colorbalance.c',
  'colorbalancechannel.c',
  'convertframe.c',
  'gstvideoaffinetransformationmeta.c',
  'gstvideodecoder.c',
  'gstvideoencoder.c',
  'gstvideofilter.c',
  'gstvideometa.c',
  'gstvideopool.c',
  'gstvideosink.c',
  'gstvideoutils.c',
  'gstvideoutilsprivate.c',
  'navigation.c',
  'video.c',
  'video-blend.c',
  'video-chroma.c',
  'video-color.c',
  'video-converter.c',
  'video-dither.c',
  'video-event.c',
  'video-format.c',
  'video-frame.c',
  'video-info.c',
  'video-multiview.c',
  'video-resampler.c',
  'video-scaler.c',
  'video-tile.c',
  'video-overlay-composition.c',
  'videoorientation.c',
  'videooverlay.c',
]

video_mkenum_headers = [
  'video.h',
  'video-format.h',
  'video-frame.h',
  'video-chroma.h',
  'video-color.h',
  'video-converter.h',
  'video-dither.h',
  'video-info.h',
  'video-resampler.h',
  'video-scaler.h',
  'video-tile.h',
  'colorbalance.h',
  'navigation.h',
]

configure_file(input : 'video-orc-dist.h',
  output : 'video-orc.h',
  configuration : configuration_data())

video_orc_c = configure_file(input : 'video-orc-dist.c',
  output : 'video-orc.c',
  configuration : configuration_data())

mkenums = find_program('video_mkenum.py')
gstvideo_h = custom_target('gstvideoenum_h',
  output : 'video-enumtypes.h',
  input : video_mkenum_headers,
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstvideo_c = custom_target('gstvideoenum_c',
  output : 'video-enumtypes.c',
  input : video_mkenum_headers,
  command : [mkenums, '@OUTPUT@', '@INPUT@'])


gstvideo = library('gstvideo',
  video_sources, gstvideo_h, gstvideo_c, video_orc_c,
  c_args : core_args,
  include_directories : core_inc,
  dependencies : [gst_dep, glib_dep],
)

video_dep = declare_dependency(link_with : gstvideo,
  sources : gstvideo_h)