paprefs_sources = [
  'paprefs.cc',
]

paprefs_dependencies = [
  giomm,
  gtkmm,
  sigc,
  libpulse,
]

executable(
  'paprefs',
  paprefs_sources,
  include_directories: configuration_inc,
  dependencies: paprefs_dependencies,
  install: true,
)

desktop_file = i18n.merge_file(
  input: 'paprefs.desktop.in',
  output: 'paprefs.desktop',
  type: 'desktop',
  po_dir: '../po',
  install: true,
  install_dir: join_paths(datadir, 'applications'),
)

install_data(
  'paprefs.glade',
  install_dir: join_paths(pkgdatadir),
)
