moduledir = join_paths(pkgdatadir, 'abacus')

configure_file(
  input: 'abacus.in',
  output: 'abacus',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

abacus_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(abacus_sources, install_dir: moduledir)
