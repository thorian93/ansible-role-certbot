# Ansible Role: Certbot

This role installs [Certbot](https://certbot.eff.org/) and manages certificates with LetsEncrypt on RHEL/CentOS, Debian/Ubuntu and Fedora servers.

[![Ansible Role: Certbot](https://img.shields.io/ansible/role/51302?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_certbot)
[![Ansible Role: Certbot](https://img.shields.io/ansible/quality/51302?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_certbot)
[![Ansible Role: Certbot](https://img.shields.io/ansible/role/d/51302?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_certbot)

## Known issues

None.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-certbot
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    certbot_staging: 'true'

Whether to get certificates against the staging or production environment.

    certbot_mode: certonly

Which certbot mode to use.

    certbot_email: "foo@bar.org"

The email corresponding to your account.

    certbot_module: apache

Which module to use to obtain certificates.

    certbot_force_renewal: 'false'

Whether to force a renewal or not.

    certbot_domains: "foo.bar"

A comma separated list of domains for the certificate.

    certbot_cert_path: "/etc/letsencrypt/live/foo.bar"

The path to the certificate folder. This can be used in other roles and `foo.bar` should be replaced by the first domain in `certbot_domains`.

## Dependencies

None.

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    role_stable_os:
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

## Example Playbook

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - ansible-role-certbot

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

This role was created in 2020 by [Thorian93](http://thorian93.de/).
