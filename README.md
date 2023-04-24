sys_fs.samba
=========

This role installs and configures Samba on Debian-based systems.

Requirements
------------

This role requires at least Ansible 2.5.

Role Variables
--------------

	samba_packages:
	  - samba

List of Samba packages to install.

	samba_global_config: {}

A config dictionary. Underscores in keys are transformed into spaces in the
template.

	samba_shares: []

A list of dictionaries describing Samba shares. Underscores in keys are
transformed into spaces in the template. The `name` key is used in the
share's section title.

Please see the [smb.conf
documentation](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html)
for information about global and share configuration options.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: samba
	  vars:
	    - samba_global_config:
		    workgroup: EXAMPLE
			server_string: '%h server'
	    - samba_shares:
		    - name: example-share
			  path: /mnt/storage/example
			  guest_ok: 'yes'
      roles:
         - sys_fs.samba

License
-------

MIT
