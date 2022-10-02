pkgname=lvm-autosnap
pkgver=0.0.1
pkgrel=1
pkgdesc=''
arch=('any')
license=('MIT')
install="lvm-autosnap.install"
depends=('lvm2')
source=(
  'cli.sh'
  'config.sh'
  'core.sh'
  'install-hook.sh'
  'lvm-autosnap'
  'lvm-autosnap.env'
  'lvm-autosnap.service'
  'lvm-autosnap.timer'
  'lvm-wrapper.sh'
  'lvol.sh'
  'runtime-hook.sh'
  'util.sh'
)
backup=(etc/lvm-autosnap.env)

package() {
  # Add core scripts
  bin_dir="${pkgdir}/usr/share/lvm-autosnap"
  install -D -m0755 "${srcdir}/cli.sh" "$bin_dir/cli.sh"
  install -D -m0755 "${srcdir}/config.sh" "$bin_dir/config.sh"
  install -D -m0755 "${srcdir}/core.sh" "$bin_dir/core.sh"
  install -D -m0755 "${srcdir}/lvm-wrapper.sh" "$bin_dir/lvm-wrapper.sh"
  install -D -m0755 "${srcdir}/lvol.sh" "$bin_dir/lvol.sh"
  install -D -m0755 "${srcdir}/util.sh" "$bin_dir/util.sh"

  # Add the CLI
  install -D -m0755 "${srcdir}/lvm-autosnap" "${pkgdir}/usr/bin/lvm-autosnap"

  # Add default config file
  install -D -m0644 "${srcdir}/lvm-autosnap.env" "${pkgdir}/etc/lvm-autosnap.env"

    # Add service to mark snapshots as not-pending once successfully booted
  install -D -m0644 "${srcdir}/lvm-autosnap.service" "${pkgdir}/usr/lib/systemd/system/lvm-autosnap.service"
  install -D -m0644 "${srcdir}/lvm-autosnap.timer" "${pkgdir}/usr/lib/systemd/system/lvm-autosnap.timer"

  # Add the initcpio hooks
  install -D -m0644 "${srcdir}/install-hook.sh" "${pkgdir}/usr/lib/initcpio/install/lvm-autosnap"
  install -D -m0644 "${srcdir}/runtime-hook.sh" "${pkgdir}/usr/lib/initcpio/hooks/lvm-autosnap"
}

sha256sums=('4a0e3ce816e7dd96871dec8a929538fabe0c65b7605c646b73de0d6e42fb399f'
            '30e41485d18518ae33f6886124e246ae7c26365dc73d9b577f7d8a474343e149'
            '1f1a94f6782fba73a6856bb0db049fd4d88a64948ccb032535a1419b7aef5330'
            'edfce930e56a1f7b4595643e1bd63f40a2abfb62c2b49dd9bb74acc63b639380'
            'bad472cc3f9112460bb60519923e5dea6efcd4da20e292a47549e322ce6eb029'
            '2f4740be82fd099192d49239d21423b8bcbaf55831c31258f29a1b8516e34760'
            'b1a9666c71ab8bc008b321a2ff4cab0ad5ead45a54ecb8c932e0fbda5dd1643f'
            'e8da40587043edc18744bd23b844edfac95f6766cf6b397fce5ddbb3560401c2'
            'bda5351c3e38688c79db2b92381fb6786a11f9664e8366bd45d5da72a83c6d96'
            'a37cd3cdd576d47fa015a10cb2d9fb69c841d192d8c8be3675fdc715226750d5'
            '3cecc12beb84ab1f289fbe3fa7266452c585d7d6fccd994e826babf69315f1e8'
            '4fb78b1d7bb233b6248d10713ba979a9c5b16faab6c33a40b7499a5eb105f31b')

