owncloud Client
==
owncloud client installation on Debian/Ubuntu based on the official setup script

Variables
--

    # Base APT repository URL.
    owncloud_apt_repo_base: 'http://download.owncloud.org/download/repositories/stable'

    # GPG fingerprint for the public key used to sign the APT repository.
    owncloud_apt_repo_key_id: 'BCECA90325B072AB1245F739AB7C32C35180350A'

    owncloud_apt_repo_key_url: '{{ owncloud_apt_repo_base + "/" +
                                   owncloud_distribution + "/"
                                   "Release.key" }}'

    # APT ``sources.list`` URL of the ownCloud ``.deb`` repository.
    owncloud_apt_repo_source: '{{ "deb " + owncloud_apt_repo_base + "/" +
                                  owncloud_distribution + "/ /" }}'

    # .. envvar:: owncloud_distribution
    #
    # Name and version of OS distribution to use for ownCloud packages.
    owncloud_distribution: '{{ owncloud_distribution_name + "_" +
                               owncloud_distribution_version }}'


    # .. envvar:: owncloud_distribution_name
    #
    # Name of the OS distribution to use for ownCloud URLs.
    owncloud_distribution_name: '{{ ansible_distribution }}'


    # .. envvar:: owncloud_distribution_version
    #
    # Version number of the OS distribution for ownCloud URLs.
    owncloud_distribution_version: '{{ ((ansible_distribution_major_version + ".0")
                                        if ansible_distribution in [ "Debian" ]
                                        else ansible_distribution_version) }}'

Example
--

Simplest way to include this role to your playbook :

    - hosts: localhost
      roles:
         - { role: vcabourdin.owncloud-client }

License
--

MIT

Known issues
--

I would be happy to **adapt this role to other platforms**. If you are interested in such feature, please [create an issue](https://github.com/vcabourdin/ansible-owncloud-client/issues/new) or, even better, a pull request :)
