# Cronic

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org/)
[![semver](https://img.shields.io/badge/SemVer-2.0.0-blue)](https://semver.org/spec/v2.0.0.html)

This is enhanced version of [cronic](https://habilis.net/cronic/) originaly created by
[Chuck Houpt](http://habilis.net/chuck/).

## A cure for Cron's chronic email problem

By [Chuck Houpt](https://habilis.net/chuck/).

The Disease:

    0 1 * * * backup >/dev/null 2>&1

The Cure:

    0 1 * * * cronic backup

> [Cronic](https://habilis.net/cronic/) is a shell script to help control
> the most annoying feature of [cron](https://en.wikipedia.org/wiki/Cron):
> unwanted emailed output, or "cram" (cron spam). If the [Unix Haters
> list](http://web.archive.org/web/20160930164205/http://www.mindspring.com/~blackhart/)
> was still active, I would submit the rant below to gain membership.
> -- [Chuck Houpt](http://habilis.net/chuck/)

## The Disease

One of the best features of cron is its automatic email - it is also its worst
feature. Cron automatically emails the output of a cron job to the user. On the
face of it, this sounds like a great idea. Cron jobs can run automatically in
the background for months at a time - so getting an email when a problem occurs
sounds useful.

Unfortunately, cron's idea of "output" is simultaneously too broad and too
narrow to actually be useful. Cron considers *any* output to be significant -
including standard output. This interacts badly with many unix commands, which
often send status info to standard out. Some commands have a quiet options, but
that can turn off all error output too. To make matters worse, cron *ignores*
command result codes, meaning that errors from quiet programs are ignored.

It is almost impossible to create a non-trivial cron job that is quiet enough
to run without output, but still reports all errors. Following the principle of
["Worse is Better"](http://www.jwz.org/doc/worse-is-better.html), the typical
solution is to sweep it all under the carpet by redirecting all output to
`/dev/null`, and hoping for the best:

    0 1 * * * backup >/dev/null 2>&1

Now when your cron job fails, you will never know about it. Using cron to
backup your files? Sorry, the cron job has been failing due to permission
errors for months - all your files are gone.

Could cron be fixed? Although almost all current implementation of cron are
open source, cron's pathological behavior has been petrified into the [Unix
standards](http://www.opengroup.org/onlinepubs/009695399/utilities/crontab.html).
So if it isn't broken, it isn't cron. The only solution left is a work-around.

## The Cure: Cronic

Download [Cronic](https://github.com/octivi/cronic/releases).

Cronic is a small shim shell script for wrapping cron jobs so that cron only
sends email when an error has occurred. Cronic defines an error as any
non-trace error output or a non-zero result code. Cronic filters
[Bash](http://www.gnu.org/software/bash/bash.html) execution traces (or
anything matching
[PS4](http://www.gnu.org/software/bash/manual/bashref.html#index-PS4-228)) from
the error output, so jobs can be run with execution tracing to aid forensic
debugging.  Cronic has no options, it simply executes its arguments.

    0 1 * * * cronic backup

With Cronic, you can turn on Bash's strict error handling and debug options
([exit on error, unset variable detection and execution
tracing](http://www.gnu.org/software/bash/manual/bashref.html#The-Set-Builtin))
to make sure problems are caught early. For example:

    #!/bin/bash

    set -o errexit -o nounset -o xtrace

    cp -rp data1 /backup
    cp -rp data2 /backup
    cp -rp data3 /backup

When an error is detected, Cronic outputs a report listing the result code,
error output, and combined trace and error output. The combined output can help
put error messages in context.  An example:

    From: user@example.net (Cron Daemon)
    To: user@example.net
    Subject: Cron <user@server> cronic backup

    Cronic detected failure or error output for the command:
    backup

    RESULT CODE: 1

    ERROR OUTPUT:
    cp: data2: Permission denied

    STANDARD OUTPUT:

    TRACE-ERROR OUTPUT:
    + cp -rp data1 /backup
    + cp -rp data2 /backup
    cp: data2: Permission denied

## Installation

### Manual

Just download and grant execution (x) permission to `cronic`

```bash
# or https://github.com/octivi/cronic/releases/latest/download/cronic if you want always latest release
sudo curl -fsSLo /usr/local/bin/cronic https://github.com/octivi/cronic/releases/download/v3-octivi-3.0.1/cronic
sudo chmod +x /usr/local/bin/cronic
```

### Ansible

One simple task to install `cronic`

```
- name: 'Install cronic'
  ansible.builtin.get_url:
    # or https://github.com/octivi/cronic/releases/latest/download/cronic if you want always latest release
    url: 'https://github.com/octivi/cronic/releases/download/v3-octivi-3.0.1/cronic'
    dest: '/usr/local/bin/cronic'
    owner: 'root'
    group: 'root'
    mode: '0755'
    # or https://github.com/octivi/cronic/releases/latest/download/cronic.sha256 if you want always latest release
    checksum: 'sha256:https://github.com/octivi/cronic/releases/download/v3-octivi-3.0.1/cronic.sha256'
  register: '__cronic_download'
  until: __cronic_download is succeeded
  retries: 5
  delay: 2
```

## Version History

- [v3-octivi](https://github.com/octivi/cronic/releases) - Refactor and fix
    errors reported by [shellcheck](https://www.shellcheck.net/).
- v3 - Use mktemp-d to avoid race-conditions and security problems.
- v2 - Corrected command evaluation, so shell meta-chars are preserved
    correctly (Thanks to Frank Wallingford for the fix).
- v1 - Initial release.

## Related Projects

Cronic isn't the only cure for cron. Cronic's main advantage it is small,
simple and a shell script. There are several C-based cron wrapper programs with
many additional capabilities and options:

- [Shush](http://web.taranis.org/shush/): a C-based cron wrapper, with multiple
    report formats, syslogging, etc.
- [Cronwrap](https://pypi.org/project/cronwrap/): a Python cron job wrapper that
    wraps jobs and enables better error reporting and command timeouts.
