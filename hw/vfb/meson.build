srcs = [
    'InitInput.c',
    'InitOutput.c',
    '../../mi/miinitext.c',
]

vfb_dep = []
vfb_glamor = []
if build_glamor
    srcs += '../../glamor/glamor_egl.c'
    vfb_dep += [
        libdrm_dep,
        gbm_dep,
    ]
    vfb_glamor += glamor
endif

xvfb_server = executable(
    'Xvfb',
    srcs,
    include_directories: inc,
    dependencies: [
        common_dep,
        vfb_dep,
    ],
    link_with: [
        vfb_glamor,
        libxserver_main,
        libxserver_fb,
        libxserver,
        libxserver_xkb_stubs,
        libxserver_xi_stubs,
        libxserver_glx,
        libglxvnd,
    ],
    install: true,
)

install_man(configure_file(
    input: 'man/Xvfb.man',
    output: 'Xvfb.1',
    configuration: manpage_config,
))
