project('gst-plugins-base', 'c', 'cpp',
  version : '1.8.0',
  meson_version : '>= 0.27.0',
  default_options : [ 'warning_level=1',
                      'c_std=gnu99',
                      'buildtype=debugoptimized' ])

gst_version = meson.project_version()
version_arr = gst_version.split('.')
gst_version_major = version_arr[0]
gst_version_minor = version_arr[1]
gst_version_micro = version_arr[2]
if version_arr.length() == 4
  gst_version_nano = version_arr[3]
else
  gst_version_nano = 0
endif

glib_req = '>= 2.40.0'
gst_req = '>= @0@.@1@.0'.format(gst_version_major, gst_version_minor)

api_version = '1.0'
soversion = 0
# maintaining compatibility with the previous libtool versioning
# current = minor * 100 + micro
# FIXME: should be able to convert string to int somehow so we can just do maths
if gst_version_micro == '0' or gst_version_micro == '1' or gst_version_micro == '2' or gst_version_micro == '3' or gst_version_micro == '4' or gst_version_micro == '5' or gst_version_micro == '6' or gst_version_micro == '7' or gst_version_micro == '8' or gst_version_micro == '9'
  libversion = '0.' + gst_version_minor + '0' + gst_version_micro + '.0'
else
  libversion = '0.' + gst_version_minor + gst_version_micro + '.0'
endif

plugins_install_dir = '@0@/gstreamer-1.0'.format(get_option('libdir'))

cc = meson.get_compiler('c')

core_conf = configuration_data()
check_headers = [
  ['HAVE_DLFCN_H', 'dlfcn.h'],
  ['HAVE_EMMINTRIN_H', 'emmintrin.h'],
  ['HAVE_INTTYPES_H', 'inttypes.h'],
  ['HAVE_MEMORY_H', 'memory.h'],
  ['HAVE_PROCESS_H', 'process.h'],
  ['HAVE_STDINT_H', 'stdint.h'],
  ['HAVE_STDLIB_H', 'stdlib.h'],
  ['HAVE_STRINGS_H', 'strings.h'],
  ['HAVE_STRING_H', 'string.h'],
  ['HAVE_SYS_SOCKET_H', 'sys/socket.h'],
  ['HAVE_SYS_STAT_H', 'sys/stat.h'],
  ['HAVE_SYS_TYPES_H', 'sys/types.h'],
  ['HAVE_SYS_WAIT_H', 'sys/wait.h'],
  ['HAVE_UNISTD_H', 'unistd.h'],
  ['HAVE_WINSOCK2_H', 'winsock2.h'],
  ['HAVE_XMMINTRIN_H', 'xmmintrin.h'],
]
foreach h : check_headers
  if cc.has_header(h.get(1))
    core_conf.set(h.get(0), 1)
  endif
endforeach

check_functions = [
  ['HAVE_DCGETTEXT', 'dcgettext', '#include<libintl.h>'],
  ['HAVE_GMTIME_R', 'gmtime_r', '#include<time.h>'],
  ['HAVE_LRINTF', 'lrintf', '#include<math.h>'],
  ['HAVE_MMAP', 'mmap', '#include<sys/mman.h>'],
]

foreach f : check_functions
  if cc.has_function(f.get(1), prefix : f.get(2))
    core_conf.set(f.get(0), 1)
  endif
endforeach

core_conf.set('SIZEOF_CHAR', cc.sizeof('char'))
core_conf.set('SIZEOF_INT', cc.sizeof('int'))
core_conf.set('SIZEOF_LONG', cc.sizeof('long'))
core_conf.set('SIZEOF_SHORT', cc.sizeof('short'))
core_conf.set('SIZEOF_VOIDP', cc.sizeof('void*'))

core_conf.set('GETTEXT_PACKAGE', '"gst-plugins-base-1.0"')
core_conf.set('PACKAGE', '"gst-plugins-base"')
core_conf.set('VERSION', '"@0@"'.format(gst_version))
core_conf.set('PACKAGE_VERSION', '"@0@"'.format(gst_version))
core_conf.set('GST_PACKAGE_NAME', '"GStreamer Base Plug-ins"')
core_conf.set('GST_PACKAGE_ORIGIN', '"Unknown package origin"')
core_conf.set('GST_API_VERSION', '"@0@"'.format(api_version))
core_conf.set('GST_INSTALL_PLUGINS_HELPER', '"/FIXME"')
core_conf.set('GST_DATADIR', '"/FIXME"')
core_conf.set('GST_LICENSE', '"LGPL"')
core_conf.set('DISABLE_ORC', 1)
# FIXME: These should be configure options
core_conf.set('DEFAULT_VIDEOSINK', '"autovideosink"')
core_conf.set('DEFAULT_AUDIOSINK', '"autoaudiosink"')

gst_plugins_base_args = ['-DHAVE_CONFIG_H']

libm = cc.find_library('m', required : false)
# X11 checks are for sys/ and tests/
x11_dep = dependency('x11', required : false)
# GLib checks are for the entire project
giounix_dep = dependency('gio-unix-2.0', version : glib_req, required : false)
glib_dep = dependency('glib-2.0', version : glib_req)
gobject_dep = dependency('gobject-2.0', version : glib_req)
gio_dep = dependency('gio-2.0', version : glib_req)

core_conf.set('HAVE_X', x11_dep.found())
core_conf.set('HAVE_GIO_UNIX_2_0', giounix_dep.found())

runcmd = run_command('pkg-config', '--variable=giomoduledir', 'gio-2.0')
if runcmd.returncode() == 0
  core_conf.set('GIO_MODULE_DIR', '"@0@"'.format(runcmd.stdout().strip()))
endif
runcmd = run_command('pkg-config', '--variable=libdir', 'gio-2.0')
if runcmd.returncode() == 0
  core_conf.set('GIO_LIBDIR', '"@0@"'.format(runcmd.stdout().strip()))
endif
runcmd = run_command('pkg-config', '--variable=prefix', 'gio-2.0')
if runcmd.returncode() == 0
  core_conf.set('GIO_PREFIX', '"@0@"'.format(runcmd.stdout().strip()))
endif

gst_plugins_base_incs = include_directories('gst-libs', '.')

# To use the subproject make subprojects directory
# and put gstreamer meson git there (symlinking is fine)
gst_dep = dependency('gstreamer-1.0', version : gst_req, required : false)
if not gst_dep.found()
  gst_proj = subproject('gstreamer')
  gst_dep = gst_proj.get_variable('gst_dep')
  gst_base_dep = gst_proj.get_variable('gst_base_dep')
  gst_net_dep = gst_proj.get_variable('gst_net_dep')
  gst_check_dep = gst_proj.get_variable('gst_check_dep')
  gst_controller_dep = gst_proj.get_variable('gst_controller_dep')
else
  gst_base_dep = dependency('gstreamer-base-1.0', version : gst_req)
  gst_net_dep = dependency('gstreamer-net-1.0', version : gst_req)
  gst_check_dep = dependency('gstreamer-check-1.0', version : gst_req)
  gst_controller_dep = dependency('gstreamer-controller-1.0', version : gst_req)
endif

vs_module_defs_dir = meson.source_root() + '/win32/common/'

subdir('gst-libs')
subdir('gst')
subdir('ext')
subdir('sys')
subdir('tools')
subdir('tests')
subdir('pkgconfig')

# Use core_conf after all subdirs have set values
configure_file(input : 'config.h.meson',
  output : 'config.h',
  configuration : core_conf)
