# NAME

Ubic::Service::ServerStarter - Helper for running psgi applications with ubic and plackup

# VERSION

version 0.001

# SYNOPSIS

    use Ubic::Service::ServerStarter;
    return Ubic::Service::ServerStarter->new({
        cmd => [
            'starman',
            '--preload-app',
            '--env' => 'development',
            '--workers' => 5,
        ],
        args => {
            interval => 5,
            port => 5003,
            signal-on-hup => 'QUIT',
            signal-on-term => 'QUIT',
        },
        ubic_log => '/var/log/app/ubic.log',
        stdout   => '/var/log/app/stdout.log',
        stderr   => '/var/log/app/stderr.log',
        user     => "www-data",
    });

# DESCRIPTION

This service is a common ubic wrap for psgi applications.
It uses plackup for running these applications.

# NAME

Ubic::Service::ServerStarter - ubic service class for running commands
with [Server::Starter](http://search.cpan.org/perldoc?Server::Starter)

# METHODS

- _args_ (optional)

Arguments to send to start_server.

- _cmd_ (required)

ArrayRef of command + options to run with server starter.  Everything passed
here will go be put after the `--` in the `start_server` command:

    start_server [ args ] -- [ cmd ]

This argument is required becasue we have to have something to run!

- _status_

Coderef to special function, that will check status of your application.

- _ubic_log_

Path to ubic log.

- _stdout_

Path to stdout log of plackup.

- _stderr_

Path to stderr log of plackup.

- _user_

User under which plackup will be started.

- _group_

Group under which plackup will be started. Default is all user groups.

- _cwd_

Change working directory before starting a daemon.

- _pidfile_

Pidfile for `Ubic::Daemon` module.

If not specified, it will be derived from service's name or from _app_name_,
if provided.

Pidfile is:

                - _pidfile_ option value, if provided;
            - `/tmp/APP_NAME.pid`, where APP_NAME is _app_name_ option value, if it's
            provided;
        - `/tmp/SERVICE_NAME.pid`, where SERVICE_NAME is service's full name.
    - `pidfile()`

    Get pidfile name.

    - `bin()`

    Get command-line with all arguments in the arrayref form.

# AUTHOR

William Wolf <throughnothing@gmail.com>

# COPYRIGHT AND LICENSE



William Wolf has dedicated the work to the Commons by waiving all of his
or her rights to the work worldwide under copyright law and all related or
neighboring legal rights he or she had in the work, to the extent allowable by
law.

Works under CC0 do not require attribution. When citing the work, you should
not imply endorsement by the author.