project('paprefs', 'cpp',
  license: 'GPL2+',
  version: '1.0',
  meson_version: '>=0.40.1'
)

mailing_list = 'pulseaudio-discuss (at) lists (dot) freedesktop (dot) org'
homepage = 'http://freedesktop.org/software/pulseaudio/paprefs/'

with_lynx = get_option('lynx')

i18n = import('i18n')

gtkmm = dependency('gtkmm-3.0')
giomm = dependency('giomm-2.4', version: '>= 2.26')
sigc = dependency('sigc++-2.0')
dbus_glib = dependency('dbus-glib-1')
libpulse = dependency('libpulse')

lynx = find_program('lynx', required: with_lynx)
tidy = find_program('tidy', required: false)

prefix = get_option('prefix')
bindir = join_paths(prefix, get_option('bindir'))
localedir = join_paths(prefix, get_option('localedir'))
datadir = join_paths(prefix, get_option('datadir'))
pkgdatadir = join_paths(datadir, meson.project_name())

conf = configuration_data()

conf.set_quoted('GETTEXT_PACKAGE', meson.project_name())
conf.set_quoted('GLADE_FILE', join_paths(pkgdatadir, 'paprefs.glade'))
conf.set_quoted('LOCALEDIR', localedir)
conf.set_quoted('MODDIR', libpulse.get_pkgconfig_variable('modlibexecdir'))
# Needs fixing on some borked OS
conf.set_quoted('SHREXT', '.so')

configure_file(
  output : 'config.h',
  configuration : conf
)

common_flags = [
  '-DHAVE_CONFIG_H',
]
add_project_arguments(common_flags, language: 'cpp')

configuration_inc = include_directories('.')

subdir('src')
subdir('po')
subdir('doc')
