DragonFly Mail Transport Agent (DMA)
=========

This role installs and configures the [DragonFly Mail Transport Agent
(DMA)](dma) to relay mail to a smarthost. If desired, an alias can be set under
`/etc/aliases` to forward *all* mail to the specified email address.

I deploy this role to machines to receive their system mail. (See [this blog
post](post) for a bit more background information.)

[dma]: https://github.com/corecode/dma
[post]: https://notebook.niklaas.eu/post/2018-04-08-from-nullmailer-to-dma/

Requirements
------------

None

Role Variables
--------------

Variable | Description
--- | ---
dma_alias_mail | Email address to relay all mail to. If set, this will create `/etc/aliases` with a single line forwarding all mail to the specified address. If not set, `/etc/aliases` remains untouched.  (default: null)
dma_insecure | If set to `true`, this will include option `INSECURE` in `/etc/dma.conf` (default: null)
dma_masquerade | If set, the sender of all mails will be masqueraded to this email address. Depending on the smarthost, this must be a valid email address for the authorised user `dma_user`. (default: null)
dma_password | If set, this will be used to authorise at the smarthost. (default: null)
dma_smarthost | The smarthost to relay mail to e.g., `smtp.gmail.com`. (mandatory, default: null)
dma_user | If set, this will be used to authorise at the smarthost (default: null)

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: dma, dma_smarthost: smtp.super-mail.com }

License
-------

MIT

Author Information
------------------

Niklaas Baudet von Gersdorff
