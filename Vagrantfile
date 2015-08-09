# -*- mode: ruby -*-
# # vi: set ft=ruby :

Vagrant.require_version '>= 1.6.0'

require_relative 'change_host_name.rb'
require_relative 'configure_networks.rb'

Vagrant.configure('2') do |config|
  # SSH in as the default 'core' user, it has the vagrant ssh key.
  config.ssh.username = 'core'

  # Always use Vagrant's insecure key
  config.ssh.insert_key = false

  # Disable the base shared folder, guest additions are unavailable.
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # Options for libvirt vagrant provider.
  config.vm.provider :libvirt do |libvirt|
    # A hypervisor name to access. Different drivers can be specified, but
    # this version of provider creates KVM machines only. Some examples of
    # drivers are kvm (qemu hardware accelerated), qemu (qemu emulated),
    # xen (Xen hypervisor), lxc (Linux Containers),
    # esx (VMware ESX), vmwarews (VMware Workstation) and more. Refer to
    # documentation for available drivers (http://libvirt.org/drivers.html).
    libvirt.driver = 'kvm'

    # The name of the server, where libvirtd is running.
    libvirt.host = ''

    # If use ssh tunnel to connect to Libvirt.
    libvirt.connect_via_ssh = false

    # Libvirt storage pool name, where box image and instance snapshots will
    # be stored.
    libvirt.storage_pool_name = 'default'
  end
end
