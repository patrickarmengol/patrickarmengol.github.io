---
title: "Creating Arch Linux Packages"
date: 2022-12-01T04:56:20Z
tags: ['linux', 'python']
---

This is not a tutorial / guide for creating Arch linux packages. I'm just jotting down some of my notes and thoughts about my experience learning how to create Arch Linux packages. 

## Background

When I first started with Linux in university, I decided I would jump into the deep end that was Arch Linux (btw). Despite my numerous trials and tribulations in understanding the system, and continued frustrations just trying to get something to work, I have been daily driving the distro ever since. Yet, I still feel like a Linux noob. I learned enough stuff to _"get by"_, never really built a deep understanding of anything. The ArchWiki is my savior. Recently, I have been learning about Python packaging and distribution, which pointed my interest towards Arch Linux packaging. 

Arch's built in package management utility is `pacman`, and I have to say I definitely prefer it over the alternatives I've tried (like `apt` and `brew`). Most of the applications/libraries you need will be available in the official repositories. But occasionally, you will need to look for something on the Arch User Repository, where regular users can share package specs via `PKGBUILD`s, with which other users can compile packages from source with `makepkg` and install with `pacman`. To install packages from the AUR, most people utilize an AUR helper utility, like `paru`. The ArchWiki warns: _"AUR packages are user-produced content. These PKGBUILDs are completely unofficial and have not been thoroughly vetted. Any use of the provided files is at your own risk."_ Even so, my experience has been that AUR packages are typically more up-to-date and function as expected. 

So, since I have been learning software development, I decided I should learn how to distribute my software on the AUR if I eventually create something useful. 


## Official Docs

The ArchWiki has extensive documentation on packaging. 

- [Creating packages](https://wiki.archlinux.org/title/Creating_packages)
- [Arch package guidelines](https://wiki.archlinux.org/title/Arch_package_guidelines)
- [Python package guidelines](https://wiki.archlinux.org/title/Python_package_guidelines)
- [VCS package guidelines](https://wiki.archlinux.org/title/VCS_package_guidelines)
- [AUR submission guidelines](https://wiki.archlinux.org/title/AUR_submission_guidelines)

I have to say, I thought the way the information was presented in these articles was confusing, disjointed, often conflicting, and lacked a lot of context. It also did not provide a tutorial-like walkthrough of building an example package; it was more of a reference. 


## Learn by Example

So I decided to look at a lot of example `PKGBUILD`s to learn from. This made things worse... Why does nobody follow the guidelines? No two `PKGBUILD`s I looked at had a similar format. Everyone just seemed to want to do their own thing. Often packages were missing essential fields like `provides`, so if someone made a variant of that package (like a VCS-synced version), pacman would not yell about a conflict. Very rarely was the `check()` function called. Python packages sometimes sourced from PyPI instead of GitHub. `pkgver()` checks sometimes did not exclude leading characters in version numbers pulled from tags. Almost every non-VCS-synced package was somewhere between 5 minor versions and 1 major version behind. Dependencies that were listed for the package rarely matched the developer specified dependencies and none had version bounding. I even searched GitHub for repos collecting the various `PKGBUILD`s that people managed and I found that even the big-name maintainers did not follow a standard way of doing things. 

I mean, lets just look at one example: [python-hatch PKGBUILD](https://github.com/archlinux/svntogit-community/blob/85686e0ca48972fe46685e207ed9b682783a2385/trunk/PKGBUILD).

```bash
# Maintainer: Santiago Torres-Arias <santiago @ usualplace>
# Contributor: Kaizhao Zhang <zhangkaizhao@gmail.com>

pkgname=python-hatch
pkgver=1.5.0
pkgrel=1
pkgdesc="A modern project, package, and virtual env manager"
arch=('any')
url="https://github.com/ofek/hatch"
license=('MIT')
depends=(
  'python' 'python-appdirs' 'python-atomicwrites' 'python-click'
  'python-colorama' 'python-coverage' 'python-pexpect' 'python-pip'
  'python-pytest' 'python-semver' 'python-setuptools' 'python-sortedcontainers'
  'python-toml' 'twine' 'python-userpath' 'python-virtualenv' 'python-wheel'
  'python-build'
)


_name=${pkgname/python-/}
source=(
  "https://files.pythonhosted.org/packages/source/${_name:0:1}/${_name}/${_name}-${pkgver}.tar.gz"
  'hatch_complete.sh'
  'hatch_complete.zsh'
)
sha256sums=('cdd9bdcf6bd8fccbde26c4f84f8fc14859d912d078cd0348d350c973bed073f4'
            'b87254c621719188907a2062b0aa3c4eb078088872d1de7d53d6a6d61a679c44'
            'a43679d72ebb7b5c029192519597eff835586d0b6ed9d1e3dfc93270b8720e71')

build() {
  cd "${srcdir}/${_name}-${pkgver}"
  python -m build
}

package() {
  cd "${srcdir}/${_name}-${pkgver}"
  PIP_CONFIG_FILE=/dev/null pip install --isolated --root="${pkgdir}" --ignore-installed --no-deps dist/*.whl
  install -Dm644 LICENSE.txt -t "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  cd "${srcdir}"

  # Tab completions.
  # via https://github.com/ofek/hatch/issues/57 and
  # https://click.palletsprojects.com/en/7.x/bashcomplete/

  # Tab completion for Bash.
  # Generated by `_HATCH_COMPLETE=source hatch > hatch_complete.sh`
  install -Dm644 hatch_complete.sh "${pkgdir}/usr/share/bash-completion/completions/${_name}"

  # Tab completion for Zsh.
  # Generated by `_HATCH_COMPLETE=source_zsh hatch > hatch_complete.zsh`
  install -Dm644 hatch_complete.zsh "${pkgdir}/usr/share/zsh/site-functions/_${_name}"
}
```

Problems: 

- The package version is 3 months old. The current version is 1.6.3
- The package description is `"A modern project, package, and virtual env manager"`; the official description is `"Modern, extensible Python project management"`
- The url points to the old repository home `https://github.com/ofek/hatch`; the official homepage is `https://hatch.pypa.io/latest/`
- Many dependencies are missing, and for some reason, `python-setuptools` is included even though hatch ships with its own backend `hatchling`
- Make depends are not seperated from regular depends
- The source is PyPI instead of straight from GitHub (which is ok according to the guidelines)
- The shell completion setup scripts are bundled in the arch package instead of being brought in [the official way](https://hatch.pypa.io/latest/cli/about/#tab-completion)
- The zsh completions are bugged because of a typo
- No check
- The build call does not specify `--no-isolation`
- Using `pip` to install instead of the PyPA standard `python -m installer`

Most of these issues have been brought up in the [bug reports](https://bugs.archlinux.org/?project=5&string=python-hatch) for the package, but it seems the maintainer is unresponsive. The system in place for bug reports seems archaic and overcomplicated. 

## Learn by Googling

Fed up with the state of the available official resources and examples, I thought maybe I could find a guide/tutorial that would lay out the info in a way I could follow (baby steps).

I found [this blog post](https://thiagowfx.github.io/2022/01/arch-linux-new-pkgbuild-workflow/), which was pretty helpful and included some tips that aren't in the docs. 


## Learn by Doing

I ended up just trying to build my own package and experimenting to see what worked and what didn't, and why what didn't, didn't. 

Here's the Arch package I ended up making for one of my silly python packages, [xkcdrandom](https://github.com/patrickarmengol/xkcdrandom), which generates a number that's [guaranteed to be random](https://xkcd.com/221/). 

```bash
# Maintainer: Patrick Armengol <patrickarmengol AT protonmail DOT com>

_name=xkcdrandom
pkgname=python-xkcdrandom
pkgver=0.0.2
pkgrel=1
pkgdesc="A random number generator made in accordance with https://xkcd.com/221/"
arch=('any')
url="https://github.com/patrickarmengol/xkcdrandom"
license=('MIT')
groups=()
depends=('python>=3.7')
makedepends=('python-build' 'python-installer' 'python-hatchling' 'python-wheel')
checkdepends=('python-pytest')
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("$_name-$pkgver.tar.gz::$url/archive/refs/tags/$pkgver.tar.gz")
noextract=()
sha256sums=('6b1b2bbbdfec9af893eb08ffbe39b7abb152de0be053982e7e215257134a978e')  # use updpkgsums to update

build() {
  cd "$_name-$pkgver"
  python -m build --wheel --no-isolation
}

check() {
  cd "$_name-$pkgver"
  PYTHONPATH="$PWD/src" pytest
}

package() {
  cd "$_name-$pkgver"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm644 LICENSE.txt -t "$pkgdir/usr/share/licenses/$pkgname"
}
```

Heck, I don't know how I can improve it. 

I also made a -git VCS-synced version:

```bash
# Maintainer: Patrick Armengol <patrickarmengol AT protonmail DOT com>

_name=xkcdrandom
pkgname=python-xkcdrandom-git
pkgver=0.0.2.r0.gc038281
pkgrel=1
pkgdesc="A random number generator made in accordance with https://xkcd.com/221/"
arch=('any')
url="https://github.com/patrickarmengol/xkcdrandom"
license=('MIT')
groups=()
depends=('python>=3.7')
makedepends=('git' 'python-build' 'python-installer' 'python-hatchling' 'python-wheel')
checkdepends=('python-pytest')
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("$_name::git+$url.git")
noextract=()
sha256sums=('SKIP')  # use updpkgsums to update

pkgver() {
  cd "$_name"
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "$_name"
  python -m build --wheel --no-isolation
}

check() {
  cd "$_name"
  PYTHONPATH="$PWD/src" pytest
}

package() {
  cd "$_name"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm644 LICENSE.txt -t "$pkgdir/usr/share/licenses/$pkgname"
}

```

## Submitting to AUR

Honestly, I did not understand the ArchWiki instructions for this step. I ended up using a tool called [aurpublish](https://github.com/eli-schwartz/aurpublish) instead. It comes with the added bonus of being able to manage all of your `PKGBUILD`s in [one repo](https://github.com/patrickarmengol/arch-packages) without the need for submodules. 


## The State of Arch Linux Python Packaging

Managing Python environments can be [notoriously complicated](https://xkcd.com/1987/). Virtual environments help simplify things by isolating installed dependencies for a project. But what if you want a Python app to be installed straight to your system? Well, a lot of guidance will tell you to avoid using `pip`. ArchWiki [recommendation](https://wiki.archlinux.org/title/Python#Package_management) is to use [pacman to install from official arch repositories](https://wiki.archlinux.org/title/System_maintenance#Use_the_package_manager_to_install_software); if it's not in the official repos, try the AUR; if it's not there, then create your own package. OK, fair enough. I like managing all of my installed software from one tool. But the Python ecosystem is so messy, this is just too difficult in some cases. What if the official repo has an outdated or bugged package? What if I one of the dependencies for the app I want is uninstallable due to a conflict with another app's dependency. There are other issues. 

For example, I want to install [copier](https://github.com/copier-org/copier). No official package exists, so I look in the AUR. Hooray, `python-copier` exists. Except... it's out-of-date by 5 months. No VCS-synced package exists. Let's make one then. Looks like I can't use `python-copier`'s `PKGBUILD` as a reference since it uses `setup.py`, which was removed by the project since. Whatever, I can still do it. Oh wait, this project uses poetry-core backend, I haven't tried that before. Oh wait again, some of the dependencies for the project are themselves not available as Arch packages. So I would have to build packages for each of those dependencies and perhaps any sub-dependencies that are missing too. Before I know it, I'm looking at a day's worth of work just to get one app installed. 

So, fuck it. I'm going to use `pipx` from now on. It installs each app in an isolated environment, but still exposes the apps to my PATH. And since it uses the ubiquitous PyPI for distribution, I'm rarely going to run into outdated/broken stuff. 


## Conclusion

Eh, I had some fun learning this stuff, but, like with most things in Linux, it came with a lot of frustration. I wish there was more standardized / correct way of doing things. There are some large-scale maintainers for arch packages, but not a lot of good systems / tools in place to enable them to manage those package specs. The barrier of entry is too high for app developers looking to make, manage, and update an Arch package for their app. Taking over outdated, buggy, or unmaintained packages is also too cumbersome and difficult. I wonder if there's a good solution. 

I think I'll continue to make packages occasionally for software that I'm fond of, but I have to say I'm not too motivated. 