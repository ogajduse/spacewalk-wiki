
# **DEPRECATED, NO LONGER USED**

# Containers in Spacewalk

An installation does not exist in mid-air. It runs on hardware, real or virtual. Which in turn sits on a desktop, hangs in a server rack or runs on a virtualisation server like VMware or Xen. It's usually surrounded by systems in that environment. And as an admin chances are you are more interested in managing that environment then the individual installations. I'm proposing sorting installations in containers which have far more information and influence then groups.


Admins usually come in groups and since not all of us are equally aware of what system is located where we keep the systems details uptodate. At least the first five. In most of the situations you can make the following statement "systemX is located in datacenterY, datacenterY is located on <address>/<floor>/<room>/etc.". This means to fill in the details of "systemX" I look up the information of "datacenterY" and fill it in for "systemX". But why? I know "systemX" is located in "datacenterY" isn't that enough?

The same can be said for other things like e.g.:
Monitoring - if I cannot reach the switch in "datacenterY" there's no point in checking if "systemX" is online, you won't be able to reach them.
Provisioning - if a node has been added to "datacenterY" it will at least need these entitlements, systems groups and config channels

The idea is to group systems into a container. The container almost behaves like a regular system object, it can have details, custom values, etc.. Any system contained in the container automatically inherits it's settings complementing or overwriting settings. This gives the opportunity to correlate information like system details in one place and gives the additional handles to manage systems.

As a physical object a container is the place the (virtual) *hardware* runs in. This can be a virtualisation server, a rack, a blade enclosure, etc.. This means you could have a container holding a container. Like an installation running in a  virtual image running on a Xen Server running on a server sitting in a rack. Because it could make thing really complicated I thought it would be easier to just have the simple relationships. So "vm->xen" and "installation->rack". This because a virtualisation cluster can be spread out over multiple locations. If a VMware cluster is spread out over 2 buildings, what's the location of the vmimage?

To begin there is a generic container which holds all installations not contained in other containers. This has as little as possible settings, memberships, etc. since any installation the container inherits these. This can lead to overriding settings that where there for a reason.

Since there is only one container to an installation an installation can be aware of that installation w/o looking at all containers to check if it's a member. This means you can ask what the container members are of an installation. This means you could extend e.g. the system.getDetails struct with containerMembers an array of structs (id,name,description). getDetails's address information can come from it's container.
