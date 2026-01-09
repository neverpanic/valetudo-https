# Ansible Playbook to set up a traefik reverse proxy for Valetudo

I use this playbook to set up a [traefik][traefik] reverse proxy on my Dreame
X40 Ultra running Valetudo so that I can access the Valetudo web interface over
TLS.

I have a DNS entry and static IP assigned to my robot, which are pre-requisites
for this to work. I use ACME with the DNS-01 validation method to issue
certificates from letsencrypt, but don't do that on the robot since my DNS
update scripts require Python, which the robot does not have. Instead, I'm
obtaining those certificates on a different machine and deploy them using
`scp(1)`.

I'm publishing this just in case you find it useful, but if things break, you
get to keep the pieces.

Since the robot does not have Python, Ansible will typically fail to run
against it — however, that is a problem that OpenWRT users also have. I am
abusing [zeerayne/ansible-openwrt][ansible-openwrt] for limited Ansible command
execution on the robot.

## License

The `zeerayne.openwrt` role is licensed under GPL-3.0.

The rest of this repository is licensed under Apache-2.0.

[traefik]: https://github.com/traefik/traefik/
[ansible-openwrt]: https://github.com/zeerayne/ansible-openwrt
