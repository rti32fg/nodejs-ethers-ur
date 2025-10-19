# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

if [[ ! -v "_source" ]]; then
  _source="npm"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="gitlab"
fi
_pkg=ethers
pkgname="nodejs-${_pkg}"
pkgver=6.13.2
pkgrel=1
_pkgdesc=(
  "A complete, compact and simple library"
  "for Ethereum and ilk, written in TypeScript."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  # 'i686'
  # 'x86_64'
  any
)
_http="https://github.com"
_ns="ethers-io"
url="${_http}/${_ns}/${_pkg}.js"
license=(
  "MIT"
)
depends=(
  'nodejs'
)
makedepends=(
  'npm'
)
provides=(
  "${_pkg}=${pkgver}"
)
conflicts=(
  "${_pkg}"
)
_npm="https://registry.npmjs.org"
_tarname="${_pkg}-${pkgver}"
_npm_sum="f6c68a31f674674e4aed782c4f08d7a4ec8bc04738eee38d3e22ec94e129000e"
_npm_sig_sum="56813cbbae6ea01f6e2028ca3834404ef80731924b39b12460155590d6740b58"
_git_sum="075a261daa20d7560e764327e0abd4d3eecba11909f03a8cee4d39aad6dea945"
_git_sig_sum="ac168c73698197e4b70125e5a6fd1afb962bc28d78075f3c498035cf8f973094"
_github_sum="075a261daa20d7560e764327e0abd4d3eecba11909f03a8cee4d39aad6dea945"
if [[ "${_source}" == "npm" ]]; then
  _src="${_npm}/${_pkg}/-/${_pkg}-${pkgver}.tgz"
  _sum="${_npm_sum}"
elif [[ "${_source}" == "git" ]]; then
  _src="${url}/archive/refs/tags/v${pkgver}.tar.gz"
  if [[ "${_git}" == "true" ]]; then
    _sum="${_git_sum}"
    if [[ "${_git_http}" == "gitlab" ]]; then
      _sig_sum="${_git_sig_sum}"
    elif [[ "${_git_http}" == "github" ]]; then
      _sum="${_github_sum}"
    fi
  fi
fi
source=(
  "${_src}"
  "LICENSE"
)
noextract=(
  "${_tarname}.tgz"
)
sha256sums=(
  "${_sum}"
  '48da2f39e100d4085767e94966b43f4fa95ff6a0698fba57ed460914e35f94a0'
)

package() {
  local \
    _npmdir \
    _npm_opts=() 
  _npm_opts=(
    # --user
    #   root
    -g
    --prefix
      "${pkgdir}/usr"
  )
  cd "${srcdir}"
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  _npmdir="${pkgdir}/usr/lib/node_modules/"
  mkdir \
    -p \
    "${_npmdir}"
  cd \
    "${_npmdir}"
  npm \
    install \
      "${_npm_opts[@]}" \
      "${srcdir}/${_pkg}-${pkgver}.tgz"
      # "${srcdir}/${_pkg}.js-${pkgver}"
}

