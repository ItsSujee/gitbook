# 📶 Virtualization

## Type 1 Hypervisor: Proxmox

The hardware in the server isn't that strong so I decided to go with a Type 1 hypervisor to compensate. [Proxmox](https://www.proxmox.com) is my hypervisor of choice because its ease of installation, use, ample documentation, and community support. Proxmox also provides a web UI to manage the VMs/Containers on the server.

## VM vs Containers

When running my applications I had to choose between running applications in VMs versus Containers. There are significant tradeoffs in the number of applications you can run and the speed & reliability of the applications.

When running VMs you get the maximum speed and reliability of the application as well as the ability to forward GPIO ports like the GPU. However, you greatly reduce the total number of applications you can run on the server. For example, my server has 4 CPUs so I could run a total of 4 VMs with each VM getting a dedicated CPU.

When running Containers you get the maximum number of applications running concurrently while reducing speed & reliability. Containers requires a maximum resource specification for virtual CPU (vCPU). This means the application can never use more than the specified vCPU when running at full utilization. Resulting in throttled app performance or even a crash. The major upside of containers is that you can run many more concurrent applications as long as the used resources is less than the total number of CPU in the server. Typically you would want the total vCPU request to be the same as the server. But, you could get away with more requested vCPU than exists in the server because applications do not use 100% of resources at all times.&#x20;
