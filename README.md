# deetsLTO
Reinterpretation of gentooLTO after deprecation 
This is a personal repository, and should not be used without modification.

# Requirements:

    app-portage/portage-bashrc-mv

"portage-bashrc-mv" is not deprecated and does receive updates; this is used for the package.cflags functionality, without this package we cannot easily filter flags from packages.

The package is required as we are using bashrc.d/42-flag-o-matic.sh, which prevents packages from filtering flags. This is not recommended as these filters are used in good faith and will cause build/runtime issues; which can be mitigated by filter the flags inside /etc/portage/package.cflags/.

# Pre-requirements before install when switching from gentooLTO

Open your `make.conf` and replace any references, such as `${GRAPHITE}` or `${FLTO}`, with the flags they define; you can check by using `portageq envvar GRAPHITE`, if you have already removed sourcing the configurations `make.conf.lto` or `make.conf.lto.defines`, this command will not work, you should look inside these files and find the relevant flags you wish to use.

