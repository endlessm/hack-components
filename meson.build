project('hack-components', version: '0.0.0')

conf = configuration_data()

cmd = run_command('sh', '-c', 'echo $FLATPAK_ARCH')
conf.set('FLATPAK_ARCH', cmd.stdout().strip())
conf.set('FLATPAK_BRANCH', get_option('flatpak_branch'))

configure_file(
    input: 'flatpak-overrides.in',
    output: 'global',
    install_dir: join_paths(get_option('datadir'), 'flatpak-overrides'),
    configuration: conf
)

install_data(
    'hack-data.ini',
    install_dir: join_paths(get_option('datadir'), meson.project_name())
)

install_data(
    'hack-backgrounds/hack-backgrounds.xml',
    install_dir: join_paths(get_option('datadir'), 'gnome-background-properties')
)

install_subdir(
    'hack-backgrounds/backgrounds',
    install_dir: join_paths(get_option('datadir'), 'backgrounds'),
    strip_directory: true
)

subdir('data')

meson.add_install_script(
    'mkdir', '-p',
    join_paths(get_option('prefix'), 'clippy'),
    join_paths(get_option('prefix'), 'hack-avatar-faces')
)
