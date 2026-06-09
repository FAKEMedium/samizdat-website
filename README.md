# Samizdat-Plugin-Website

Web hosting (virtual host) management for Samizdat. An **offerable** Samizdat module (clonable/hostable; can be offered to
customers). Extracted from the Samizdat monorepo with history; installs as a
standalone CPAN/pkg distribution.

## Layout

    lib/Samizdat/Plugin/Website.pm        routes + helper
    lib/Samizdat/Controller/Website.pm    request handlers
    lib/Samizdat/Model/Website.pm         business logic / data access
    lib/Samizdat/resources/templates/website/   views (install to site_perl)
    lib/Samizdat/resources/locale/website/      per-module translations

Resources install under `site_perl/Samizdat/resources/...`, where the core
resolver (`$app->resource(...)`) finds them.

## Dependencies

- **Samizdat** (core) — provides `Samizdat::Model::Cache` and the resource
  resolver. Not yet on CPAN; install the core dist or put it on `PERL5LIB`.
- Mojolicious.

## Install

    perl Makefile.PL
    make && make test          # core (Samizdat) must be on PERL5LIB
    make install               # or: make install INSTALL_BASE=/path/to/prefix

Enable it in `samizdat.yml` via `extraplugins: [Website]`.
