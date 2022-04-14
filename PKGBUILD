#!/bin/bash

# Disable various shellcheck rules that produce false 
# Repository rules should be added to the .shellcheckr
# repository root directory, see https://github.com/ko
# and https://archiv8.github.io for further informatio
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

java_=11
pkgname="jdk${java_}-graalvm-bin"
pkgver=22.0.0.2
pkgrel=1
pkgdesc="Universal virtual machine for running applications written in a variety of languages (JVM-based, LLVM-based, or other), Java ${java_} version"
arch=('x86_64'
      'aarch64')
url='https://www.graalvm.org/'
license=('custom')
depends=('java-runtime-common'
         'java-environment-common')
makedepends=()
optdepends=("graal-nodejs-jdk${java_}-bin: Node.js component (used to be bundled with this package before the 21.1.0 release)")
provides=("java-runtime=${java_}"
          "java-environment=${java_}")
options=('staticlibs')
install="$pkgname.install"
source=('graalvm-rebuild-libpolyglot.hook')
sha512sums=('SKIP')
source_x86_64=("https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-${pkgver}/graalvm-ce-java${java_}-linux-amd64-${pkgver}.tar.gz")
source_aarch64=("https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-${pkgver}/graalvm-ce-java${java_}-linux-aarch64-${pkgver}.tar.gz")
sha512sums=('30765efa2e1115fc6fe32dbae12994e7397a54fa572a121fa010baf5f95539ffaf39dbdea730fa137856aee591ff2d0f29f539cfd9608633408ba1687f561c1a')
sha512sums_x86_64=('b282fcd638407c5301613069216a09dedac1a5f4b17e74db16c39bc788b327493853968f5129727312602ca02778517a15335ecac5ebebfbbea0d9c316f529c3')
sha512sums_aarch64=('d37225957defe4e11cee24cd5cabd2d9af353bb4b8f6fccf07a2a6ed06027ac6c0df18b9aeb1c7f2e1d19023673a5c6c920bec880b68f21bab0e9d82e6611873')

package() {
    cd "graalvm-ce-java${java_}-${pkgver}"
    mkdir -p "$pkgdir/usr/lib/jvm/java-${java_}-graalvm/"
    cp -a -t "$pkgdir/usr/lib/jvm/java-${java_}-graalvm/" *
    install -DTm644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    sed "s/JAVA/${java_}/g" < "../graalvm-rebuild-libpolyglot.hook" > "graalvm-jdk${java_}-rebuild-libpolyglot.hook"
    install -DTm644 "graalvm-jdk${java_}-rebuild-libpolyglot.hook" "$pkgdir/usr/share/libalpm/hooks/graalvm-jdk${java_}-rebuild-libpolyglot.hook"
}
