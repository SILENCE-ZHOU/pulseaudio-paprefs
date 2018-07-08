doc_conf = configuration_data()
doc_conf.set('PACKAGE_VERSION', meson.project_version())
doc_conf.set('PACKAGE_BUGREPORT', mailing_list)
doc_conf.set('PACKAGE_URL', homepage)

readme_html = configure_file(
  input: 'README.html.in',
  output: 'README.html',
  configuration: doc_conf,
)

if tidy.found()
  test('XHTML documentation uses correct mark-up', tidy, args: ['-e', readme_html])
endif

if with_lynx
  custom_target(
    'README',
    input: readme_html,
    output: 'README',
    command: [find_program('./html2txt'), '@INPUT@'],
    capture: true,
    build_by_default: true,
  )
endif
