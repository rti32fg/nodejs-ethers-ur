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

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_source="npm"
_pkg="ethers"
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
if [[ "${_source}" == "npm" ]]; then
  _src="${_npm}/${_pkg}/-/${_pkg}-${pkgver}.tgz"
  _sum="ciao"
elif [[ "${_source}" == "github" ]]; then
  _src="${url}/archive/refs/tags/v${pkgver}.tar.gz"
  _sum="ciao"
fi
source=(
  "${_src}"
  "LICENSE"
)
noextract=(
  "${_pkg}-${pkgver}.tgz"
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

