# active-perl5
Legacy ActivePerl5 Windows Installation Binaries


PPM HTTPS / TLS HOTFIX:
=======================

    # C:\Perl64\lib\ActivePerl\PPM\Web.pm

    sub web_ua {
        unless ($ua) {
            my $perl_version = ActivePerl::perl_version();
            $ua = ActivePerl::PPM::Web::UA->new(
                agent      => "PPM/$ActivePerl::PPM::VERSION ActivePerl/$perl_version ($^O) ",
                env_proxy  => 1,
                keep_alive => 1,

                # ADDED
                # PPM HOTFIX for HTTPS / TLS
                ssl_opts   => { verify_hostname => 0 },
                protocols_allowed => ['http','https'],
            );

           # ...

        }

        return $ua;
    }

