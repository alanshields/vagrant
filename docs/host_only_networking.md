---
layout: documentation
title: Documentation - Host-Only Networking
---
# Host-Only Networking

Host-Only networking is a feature of VirtualBox which allows multiple
virtual machines to communicate with each other through a network via
the host machine. The network created by host-only networking is private
to the VMs involved and the host machine. The outside world cannot
join this network.

Vagrant allows users to assign a static IP to a VM, which is then
setup using host-only networking.

<div class="info">
  <h3>Supported Operating Systems</h3>
  <p>
    Since setting up host-only networking requires configuring the OS to
    use the new interface, this is a system-specific behavior. Currently,
    Vagrant supports Debian/Ubuntu, Gentoo, and RedHat.
  </p>
  <p>
    If you'd like another OS supported, you can add it yourself using a
    <a href="/docs/systems.html">custom system</a> or you can get in touch
    with a Vagrant developer and assist us in adding it to the core.
  </p>
</div>

## Assigning an IP

Assigning an IP to a virtual machine using Vagrant is simple enough,
using a single function within the Vagrantfile:

{% highlight ruby %}
Vagrant::Config.run do |config|
  config.vm.network("33.33.33.10")
end
{% endhighlight %}

The above will setup the VM with that specific IP. It is up to the user
to make sure that no static IPs will collide with other virtual machines.

<div class="info">
  <h3>Avoid Router-only IPs</h3>
  <p>
    Some IP/subnets are reserved by routers, and if the static IP you attempt to
    use conflicts with your router, it may fail to work for no obvious reason.
    The IPs are typically `192.168.0.x` and `10.0.0.x`. This is why the examples
    use `33.33.33.x`, which has been found to be very reliable.
  </p>
</div>

## Multiple Networks

By default, Vagrant uses a netmask of `255.255.255.0`. This means that
as long as the first three parts of the IP are equivalent, VMs will join
the same network. So if two VMs are created with IPs `33.33.33.10` and
`33.33.33.11`, they will be networked together. However, if a VM is
created with an IP of `33.33.34.10`, it will be on a separate network
and will not be able to communicate with the other VMs.

A custom netmask can also be used, although a netmask of `255.255.255.0`
should be sufficient in most cases. An example of using a custom netmask
is shown below:

{% highlight ruby %}
Vagrant::Config.run do |config|
  config.vm.network("33.33.34.10", :netmask => "255.255.0.0")
end
{% endhighlight %}

