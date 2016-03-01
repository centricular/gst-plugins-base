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

video_headers = [
  'colorbalance.h',
  'colorbalancechannel.h',
  'navigation.h',
  'video.h',
  'video-event.h',
  'video-format.h',
  'video-chroma.h',
  'video-color.h',
  'video-converter.h',
  'video-dither.h',
  'video-info.h',
  'video-frame.h',
  'video-scaler.h',
  'video-tile.h',
  'gstvideosink.h',
  'gstvideofilter.h',
  'gstvideometa.h',
  'gstvideoaffinetransformationmeta.h',
  'gstvideopool.h',
  'videoorientation.h',
  'videooverlay.h',
  'gstvideodecoder.h',
  'gstvideoencoder.h',
  'gstvideoutils.h',
  'video-resampler.h',
  'video-blend.h',
  'video-overlay-composition.h',
  'video-multiview.h',
]
install_headers(video_headers, subdir : 'gstreamer-1.0/gst/video/')

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
  install : true,
  install_dir : 'include/gstreamer-1.0/gst/video/',
  command : [mkenums, '@OUTPUT@', '@INPUT@'])

gstvideo_c = custom_target('gstvideoenum_c',
  output : 'video-enumtypes.c',
  input : video_mkenum_headers,
  depends : [gstvideo_h],
  command : [mkenums, '@OUTPUT@', '@INPUT@'])


gstvideo = library('gstvideo-@0@'.format(api_version),
  video_sources, gstvideo_h, gstvideo_c, video_orc_c,
  c_args : gst_plugins_base_args,
  include_directories : gst_plugins_base_incs,
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [gst_base_dep, gst_dep, glib_dep, libm],
  # Only used with MSVC
  module_defs_file: meson.source_root() + '/win32/common/libgstvideo.def',
)
# TODO: generate gir

video_dep = declare_dependency(link_with : gstvideo,
  sources : gstvideo_h)
