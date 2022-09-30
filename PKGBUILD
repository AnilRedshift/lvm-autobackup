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

sha256sums=('1392ed0bf42f385ccac5b884c276c2a7bf76d7c38b707ef312c7784cbcb33fb0'
            '30e41485d18518ae33f6886124e246ae7c26365dc73d9b577f7d8a474343e149'
            'e6e1bfc990b6f14a654c67f32c4aedce93dd3a87ef6aeb1a1078753fc1e1bed9'
            '3768f5fd32b7dd9dfdeec92a017be947e1c8634e7570fd78bec534ef3b13e8ec'
            'bad472cc3f9112460bb60519923e5dea6efcd4da20e292a47549e322ce6eb029'
            '2f4740be82fd099192d49239d21423b8bcbaf55831c31258f29a1b8516e34760'
            'b1a9666c71ab8bc008b321a2ff4cab0ad5ead45a54ecb8c932e0fbda5dd1643f'
            'e8da40587043edc18744bd23b844edfac95f6766cf6b397fce5ddbb3560401c2'
            'bda5351c3e38688c79db2b92381fb6786a11f9664e8366bd45d5da72a83c6d96'
            'a37cd3cdd576d47fa015a10cb2d9fb69c841d192d8c8be3675fdc715226750d5'
            'e2f29d12ffe02adff1896ec88bf5dd8ee45ce103ff71fc6522791097af76c66b'
            '4fb78b1d7bb233b6248d10713ba979a9c5b16faab6c33a40b7499a5eb105f31b')

