In-order to use your Computing environment online with multiple devices; and, in-order to provide a HTTP(s) interface, the system requires networking support for those who are installing it on a local workstation or computer, that is not otherwise set-up as a webserver.

To achieve this, [WireGuard](https://en.wikipedia.org/wiki/WireGuard) based [TailScale](https://tailscale.com/) provides the means to set-up networking between your devices which then means you can access and use your personal-host on all of your devices, anywhere on the internet.

You can also set-up networking configurations to support your domain name and access controlled public services.  This is particularly important for Social Web applications.

If you are looking for an open-source alternative to the [Tailscale Control server](https://tailscale.com/blog/how-tailscale-works, [Headscale](https://headscale.net/) is a solution that provides that option. 

In some implementations, it may be helpful to set-up a cheap VPS to support Public DNS.

In future, it is hoped that a VAD package will be produced to support this functionality from within Virtuoso.