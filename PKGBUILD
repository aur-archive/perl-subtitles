# Contributor: Sebastien Vasey <sebastien dot vasey at gmail dot com>
pkgname=perl-subtitles
pkgver=1.04
pkgrel=1
pkgdesc="Simple command line tool to re-time and convert subtitle files"
arch=(i686 x86_64)
url="http://search.cpan.org/dist/Subtitles/"
license=('PerlArtistic')
depends=('perl>=5.10.0')
options=(!emptydirs)
source=("http://search.cpan.org/CPAN/authors/id/K/KA/KARASIK/Subtitles-1.04.tar.gz")
md5sums=("c6ce28e1c0c0f74fb79dbe91005933bd")
install="${pkgname}.install"

build() {
  cd "$srcdir/Subtitles-$pkgver"

  # install module in vendor directories.
  PERL_MM_USE_DEFAULT=1 perl Makefile.PL INSTALLDIRS=vendor || return 1
  make || return 1
}

package() {
  cd "$srcdir/Subtitles-$pkgver"
  make install DESTDIR="$pkgdir/" || return 1

  # remove perllocal.pod and .packlist
  find "$pkgdir" -name perllocal.pod -delete
  find "$pkgdir" -name .packlist -delete
}

