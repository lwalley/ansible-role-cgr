# Ansible Role: Cgr

Installs and manages packages with [Cgr][cgr] on Mac OS X. An alternative
to `composer global require`.

Does not automatically remove packages, see [Cgr README][cgr] for instructions
on removing packages. Remember to also remove symlink if you defined bin name
and path for the package.

## Requirements

[Composer][composer] must be installed on the system prior to running this role
(suggested role: `geerlingguy.homebrew`).

WARNING: [Oh My Zsh's composer plugin][oh-my-zsh] defines `cgr` alias. If you
have enabled the Oh My Zsh composer plugin you may want to `unalias cgr`.

## Role Variables

Available variables with example values are listed below, for default values see
[`defaults/main.yml`](defaults/main.yml)):

    cgr_path: /usr/local/bin/cgr
    cgr_keep_updated: yes
    cgr_version: ~2.0
    cgr_packages:
      - name: drush/drush
        release: ~8.0
        # If you want to run cgr update and update version in composer.lock;
        # without update, version is locked after install.
        keep_updated: yes
        # If you want an additional global executable symlink add bin hash:
        bin: { name: drush, path: /usr/local/bin/drush }
      - name: pantheon-systems/terminus
        release: ~1.8
        keep_updated: yes
        bin: { name: terminus, path: /usr/local/bin/terminus }

## Dependencies

None.

## Example Playbook

    - hosts: localhost
      roles:
         - { role: lwalley.cgr }

## License

MIT

[cgr]: https://github.com/consolidation/cgr
[composer]: https://getcomposer.org
[oh-my-zsh]: https://github.com/robbyrussell/oh-my-zsh
