# Dist::Zilla

> Document： [http://dzil.org/](http://dzil.org/)

Dist::Zilla is a program to make it easier to write, package, manage, and release free software. It's targeted at libraries written in the Perl programming language and released to the CPAN.

## Install

```text
cpanm Dist::Zilla
```

## Customizing the Minting Process

### Setup

```text
dzil setup
```

### Create a default file

1. create default direcory

   ```text
   mkdir -p ~/.dzil/profiles/default
   ```

2. create three files: **profile.ini**, **Module.pm**, **plugins.ini**

profile.ini

```perl
[TemplateModule/:DefaultModuleMaker]
template = Module.pm
[DistINI]
append_file = plugins.ini
```

plugins.ini

```text
[@Basic]
[FakeRelease]

; pod
[PodWeaver]
[PodSyntaxTests]
[PodCoverageTests]
[ReadmeFromPod]
[ReadmeAnyFromPod /MarkdownInRoot]
filename = Readme.md

; Version
[Git::NextVersion]
first_version = 0.001
version_by_branch = 0
version_regexp = ^v(.+)$

; Plans
[GenerateFile]
filename = todo/{{ $dist->name }}-plan.txt
name_is_template = 1
content_is_template = 1
content = # Outlines the plan of {{ $dist->name }}
content =·
content = Item 1: Think of an idea!
content = Item 2: Think of an idea!
```

Module.pm

```perl
package {{$name}};
# ABSTRACT: turns baubles into trinkets

use Modern::Perl;
use Data::Dumper;
use IO::All -utf8;
use Cwd qw(abs_path);

use Moose;
use MooseX::StrictConstructor;
use MooseX::Method::Signatures;
use Carp 'croak';
use namespace::autoclean;

=pod

=head1 SYNOPSIS

  ...

=method method

method description

=attr att_1

attr description

=head1 SEE ALSO

=cut

no Moose;
__PACKAGE__->meta->make_immutable;

1;
```

## Distifying Your Profile

```text
dzil new My::Module
dzil build 
dzil test
dzil release
```

## Caveats

* version format as "v\(.+\)$", for example `git tags v1.000`
* podweaver will induce error in podsyntax

