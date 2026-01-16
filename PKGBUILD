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

_evmfs_available="$(
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
if [[ ! -v "_npm" ]]; then
  if [[ "${_evmfs}" == "true" ]]; then
    _npm="true"
    _git_service="github"
  elif [[ "${_evmfs}" == "false" ]]; then
    _npm="false"
    _git="false"
    _git_service="gitlab"
  fi
fi
if [[ ! -v "_source" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _source="npm"
  elif [[ "${_npm}" == "false" ]]; then
    _source="gitlab"
  fi
fi
if [[ ! -v "_git" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _git="false"
  elif [[ "${_npm}" == "false" ]]; then
    _git="true"
  fi
fi
if [[ ! -v "_git_http" ]]; then
  if [[ "${_git_service}" == "github" ]]; then
    _git_http="github"
  elif [[ "${_git_service}" == "gitlab" ]]; then
    _git_http="gitlab"
  fi
fi
if [[ ! -v "_ns" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _ns="ethers-io"
  elif [[ "${_npm}" == "false" ]]; then
    _ns="themartiancompany"
  fi
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _archive_format="tgz"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      if [[ "${_git}" == "true" ]]; then
        _archive_format="bundle"
      elif [[ "${_git}" == "false" ]]; then
        _archive_format="tar.gz"
      fi
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="tar.gz"
      if [[ "${_git_http}" == "github" ]]; then
        _archive_format="zip"
      fi
    fi
  fi
fi
_node="nodejs"
_pkg=ethers
pkgname="${_node}-${_pkg}"
pkgver=6.13.2
_commit="1a51af85397283601db77ca61d5596b145e7f2cb"
pkgrel=9
_pkgdesc=(
  "A complete, compact and simple library"
  "for Ethereum and ilk, written in TypeScript."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  # 'i686'
  # 'x86_64'
  "any"
)
_http="https://${_git_http}.com"
url="${_http}/${_ns}/${_pkg}.js"
license=(
  "MIT"
)
depends=(
  "${_node}"
)
makedepends=(
  "${_node}"
)
if [[ "${_npm}" == "true" ]]; then
  makedepends+=(
    'npm'
  )
fi
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    'git'
  )
fi
provides=(
  "${_pkg}=${pkgver}"
)
conflicts=(
  "${_pkg}"
)
if [[ "${_npm}" == "true" ]]; then
  _tag_name="pkgver"
  _tag="${pkgver}"
elif [[ "${_npm}" == "false" ]]; then
  _tag_name="commit"
  _tag="${_commit}"
fi
_tarname="${_pkg}-${pkgver}"
_tarfile="${_tarname}.${_archive_format}"
_npm_sum="f6c68a31f674674e4aed782c4f08d7a4ec8bc04738eee38d3e22ec94e129000e"
_npm_sig_sum="c788b68873bf6bf5cdbceae61aa51f4a8b453033c31550179fe0ea27185271d2"
_github_sum="075a261daa20d7560e764327e0abd4d3eecba11909f03a8cee4d39aad6dea945"
_github_sig_sum="ac168c73698197e4b70125e5a6fd1afb962bc28d78075f3c498035cf8f973094"
_gitlab_sum="SKIP"
_gitlab_sig_sum="SKIP"
_bundle_sum="SKIP"
_bundle_sig_sum="SKIP"
if [[ "${_npm}" == "true" ]]; then
  _sum="${_npm_sum}"
  _sig_sum="${_npm_sig_sum}"
elif [[ "${_npm}" == "false" ]]; then
  if [[ "${_git}" == "false" ]]; then
    if [[ "${_source}" == "github" ]]; then
      _sum="${_github_sum}"
      _sig_sum="${_github_sig_sum}"
    elif [[ "${_source}" == "gitlab" ]]; then
      _sum="${_gitlab_sum}"
      _sig_sum="${_gitlab_sig_sum}"
    fi
  elif [[ "${_git}" == "true" ]]; then
    _sum="${_bundle_sum}"
    _sig_sum="${_bundle_sig_sum}"
  fi
fi
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_bundle_uri="${_evmfs_dir}/${_bundle_sum}"
_bundle_src="${_tarfile}::${_bundle_uri}"
_evmfs_npm_uri="${_evmfs_dir}/${_npm_sum}"
_evmfs_npm_src="${_tarfile}::${_evmfs_npm_uri}"
_evmfs_sig_uri="${_evmfs_dir}/${_sig_sum}"
_evmfs_sig_src="${_tarfile}.sig::${_evmfs_sig_uri}"
_bundle_sig_uri="${_evmfs_dir}/${_bundle_sig_sum}"
_bundle_sig_src="${_tarfile}.sig::${_bundle_sig_uri}"
_npm_sig_uri="${_evmfs_dir}/${_npm_sig_sum}"
_npm_sig_src="${_tarfile}.sig::${_npm_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=(
  "LICENSE"
)
sha256sums=(
  '48da2f39e100d4085767e94966b43f4fa95ff6a0698fba57ed460914e35f94a0'
)
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_npm_uri}"
    _sig_src="${_npm_sig_src}"
    _sig_sum="${_npm_sig_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="${_bundle_uri}"
      _sum="${_bundle_sum}"
      _sig_src="${_bundle_sig_src}"
      _sig_sum="${_bundle_sig_sum}"
    elif [[ "${_git}" == "false" ]]; then
      _uri="${_evmfs_uri}"
      _sig_src="${_evmfs_sig_src}"
    fi
  fi
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/@${_ns}/${_pkg}/-/${_tarfile}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="git+${url}#${_tag_name}=${_tag}?signed"
    elif [[ "${_git}" == false ]]; then
      _uri=""
      if [[ "${_git_service}" == "github" ]]; then
        if [[ "${_tag_name}" == "commit" ]]; then
          _uri="${url}/archive/${_commit}.${_archive_format}"
          _sum="${_github_sum}"
        fi
      elif [[ "${_git_service}" == "gitlab" ]]; then
        if [[ "${_tag_name}" == "commit" ]]; then
          _uri="${url}/-/archive/${_tag}/${_tag}.${_archive_format}"
        fi
      fi
    fi
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_npm}" == "true" ]]; then
  noextract=(
    "${_tarfile}"
  )
fi

package() {
  local \
    _npmdir \
    _npm_opts=() 
  _npm_opts=(
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
      "${srcdir}/${_tarfile}"
}
