# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_os="$( \
  uname \
    -o)"
_offline="false"
if [[ ! -v "_git" ]]; then
  _git="false"
fi
_py="python"
_pkg=android-utils
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
pkgver='0.0.0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1.1.1'
_commit="c0d0755ba29b23fca1392d3c91ec7e748df0e3e0"
pkgrel=2
_pkgdesc=(
  "Various android utility commands."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  "any"
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  "AGPL3"
)
depends=(
  "libcrash-bash"
)
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  'make'
  "${_py}-docutils"
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  url="file://${HOME}/${pkgname}"
fi
_archive_sum="616b4890d280b806874cc8a4fb41724b53c8d0191411ee145e81aae292a8b172"
_archive_sig_sum="376aa9818697ee2e419d93711bf5bebdc4987dc64c61394d51655c6de70186cb"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_archive_uri="${_evmfs_dir}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.tar.gz::${_evmfs_archive_uri}"
_archive_sig_uri="${_evmfs_dir}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.tar.gz.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}"
  )
  sha256sums+=(
    'SKIP'
  )
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum='b245547bdcdbfeb09f400305a4b515b6d49635be90f560a39302761fc2688571'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="fa59d8028cd65d978674f117ec0315dadef9f2f47e6b62937c352322ec03662a"
  fi
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)


check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgbase}-docs/"
}

# vim: ft=sh syn=sh et
