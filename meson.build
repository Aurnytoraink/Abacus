project('abacus',
          version: '0.1.0',
    meson_version: '>= 0.59.0',
  default_options: [ 'warning_level=2',
                     'werror=false',
                   ],
)

app_id = 'com.github.Aurnytoraink.Abacus'
appname = 'Abacus'

author = 'Mathieu Heurtevin'
authoremail = 'mathieu.heurtevinruiz@protonmail.com'
website = 'https://github.com/Aurnytoraink/Abacus'


# NOTE: if you contributed, feel free to add your name and email address here
contributors = '\n'.join([
    'Mathieu Heurtevin (Aurnytoraink) &lt;mathieu.heurtevinruiz@protonmail.com&gt;'
])


translators = '\n'.join([
    'French: Mathieu Heurtevin (Aurnytoraink) &lt;mathieu.heurtevinruiz@protonmail.com&gt;'
])

message('Looking for dependencies')
dependency('glib-2.0')
dependency('gobject-introspection-1.0', version: '>=1.35.9')
dependency('gtk4', version :'>=4.6.0')
dependency('libadwaita-1', version :'>=1.1.0')

pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
# conf.set('VERSION', ''.join([run_command(['git', 'describe', '--long', '--tags']).stdout(), get_option('profile')]))
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)
conf.set('PACKAGE_URL', website)
conf.set('DATA_DIR', pkgdatadir)
conf.set('APPID', app_id)
conf.set('VERSION', meson.project_version())
conf.set('CONTRIBUTORS', contributors)
conf.set('TRANSLATORS', translators)
conf.set('author', author)
conf.set('appname', appname)

i18n = import('i18n')
gnome = import('gnome')



subdir('data')
subdir('src')
subdir('po')

gnome.post_install(
  glib_compile_schemas: true,
  gtk_update_icon_cache: true,
  update_desktop_database: true,
)
