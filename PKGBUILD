# Maintainer: Peter han
# Inspired by Bidossessi Sodonon's script

pkgname=odoo_8.0
pkgver=20141007_000207
pkgrel=1
pkgdesc="Advanced OpenSource ERP and CRM server"
url=http://odoo.com/
arch=('any')
license=(GPLv3)
replaces=('openerp-server' 'openerp-web' 'openerp')
depends=(
    'gzip'
    'postgresql'
    'python2'
    'python2-dateutil'
    'python2-feedparser'
    'python2-docutils'
    'python2-pillow'
    'python2-gdata'
    'python2-ldap'
    'python2-lxml'
    'python2-mako'
    'python2-jinja'
    'python2-openid'
    'python2-psutil'
    'python2-psycopg2'
    'python2-babel'
    'python2-pychart'
    'python2-pydot'
    'python2-pyparsing'
    'python2-egenix-mx-base'
    'python2-reportlab'
    'python2-simplejson'
    'python2-pytz'
    'python2-vatnumber'
    'python2-vobject'
    'python2-pywebdav'
    'python2-werkzeug'
    'python2-xlwt'
    'python2-mock'
    'python2-unittest2'
    'python2-yaml'
    'zsi'
    'python2-decorator'
    'python2-requests'
    'python2-pypdf'
    'python2-passlib'
)
optdepends=(
    'wkhtmltopdf: Webkit reports'
)
source=(
"http://nightly.odoo.com/8.0/nightly/src/${pkgname}-${pkgver//_/-}.tar.gz"
openerp.confd
openerp-server.conf
openerp.service
)
backup=('etc/openerp/openerp-server.conf')
install=openerp.install

package()
{
  cd ${srcdir}/openerp-8.0-8843974
  # Force package data inclusion
  sed -i -e s/#include_package_data/include_package_data/ setup.py
  python2 setup.py install --root="${pkgdir}"
  mkdir ${pkgdir}/etc/{conf.d,openerp} -p
  mkdir ${pkgdir}/usr/share -p
  mkdir ${pkgdir}/usr/lib/systemd/system/ -p
  mkdir ${pkgdir}/usr/share/man/{man1,man5} -p
  # Remove useless /usr/openerp directory
  rm -rf ${pkgdir}/usr/openerp
  # Add server configs
  install -Dm 644 ${srcdir}/openerp.confd ${pkgdir}/etc/conf.d/openerp
  install -Dm 644 ${srcdir}/openerp-server.conf ${pkgdir}/etc/openerp/openerp-server.conf
  install -Dm 644 ${srcdir}/openerp.service ${pkgdir}/usr/lib/systemd/system/openerp.service
}
md5sums=('ee87eb3b2648d482c59186e624113f70'
         'effb44e444602a0e59f8fe5b4ebc47b4'
	 'c4b87d20b96c44ce38c85d9582924356'
         '3fd6f291a4ca289e3d1354e4e09a1d70')
