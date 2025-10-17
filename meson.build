project(
    'clipboard-indicator',
    'vala', 'c',
    version: '1.1.0'
)

gnome = import('gnome')
gettext_name = meson.project_name()
i18n = import('i18n')

prefix = get_option('prefix')
datadir = join_paths(prefix, get_option('datadir'))
libdir = join_paths(prefix, get_option('libdir'))

add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format(gettext_name), language:'c')
add_project_arguments('-DG_LOG_DOMAIN="jeremypw.clipboard.indicator"', language:'c')

config_data = configuration_data()
config_data.set_quoted('LOCALEDIR', join_paths(get_option('prefix'), get_option('localedir')))
config_data.set_quoted('GETTEXT_PACKAGE', meson.project_name())
config_file = configure_file(
    input: 'src/Config.vala.in',
    output: '@BASENAME@',
    configuration: config_data
)

subdir('data')
# subdir('po')
subdir('src')

gnome.post_install(glib_compile_schemas: true)