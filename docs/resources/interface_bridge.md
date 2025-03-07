# routeros_interface_bridge (Resource)


## Example Usage
```terraform
resource "routeros_interface_bridge" "bridge" {
  name           = "bridge"
  vlan_filtering = true
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Changing the name of this resource will force it to be recreated.
	> The links of other configuration properties to this resource may be lost!
	> Changing the name of the resource outside of a Terraform will result in a loss of control integrity for that resource!

### Optional

- `add_dhcp_option82` (Boolean) Whether to add DHCP Option-82 information (Agent Remote ID and Agent Circuit ID) to DHCP packets. Can be used together with Option-82 capable DHCP server to assign IP addresses and implement policies. This property only has effect when dhcp-snooping is set to yes.
- `admin_mac` (String) Static MAC address of the bridge. This property only has effect when auto-mac is set to no.
- `ageing_time` (String) How long a host's information will be kept in the bridge database.
- `arp` (String) Address Resolution Protocol mode:
	* disabled - the interface will not use ARP
	* enabled - the interface will use ARP
	* local-proxy-arp - the router performs proxy ARP on the interface and sends replies to the same interface
	* proxy-arp - the router performs proxy ARP on the interface and sends replies to other interfaces
	* reply-only - the interface will only reply to requests originated from matching IP address/MAC address combinations which are entered as static entries in the ARP table. No dynamic entries will be automatically stored in the ARP table. Therefore for communications to be successful, a valid static entry must already exist.
- `arp_timeout` (String) ARP timeout is time how long ARP record is kept in ARP table after no packets are received from IP. Value auto equals to the value of arp-timeout in IP/Settings, default is 30s. Can use postfix ms, s, M, h, d for milliseconds, seconds, minutes, hours or days. If no postfix is set then seconds (s) is used.
- `auto_mac` (Boolean) Automatically select one MAC address of bridge ports as a bridge MAC address, bridge MAC will be chosen from the first added bridge port. After a device reboot, the bridge MAC can change depending on the port-number.
- `comment` (String)
- `dhcp_snooping` (Boolean)
- `disabled` (Boolean)
- `ether_type` (String) This property only has effect when vlan-filtering is set to yes.
- `fast_forward` (Boolean)
- `forward_delay` (String) Time which is spent during the initialization phase of the bridge interface (i.e., after router startup or enabling the interface) in listening/learning state before the bridge will start functioning normally.
- `frame_types` (String) Specifies allowed frame types on a bridge port. This property only has effect when vlan-filtering is set to yes.
- `igmp_snooping` (Boolean) Enables multicast group and port learning to prevent multicast traffic from flooding all interfaces in a bridge.
- `igmp_version` (Number) Selects the IGMP version in which IGMP general membership queries will be generated. This property only has effect when igmp-snooping is set to yes.
- `ingress_filtering` (Boolean) Enables or disables VLAN ingress filtering, which checks if the ingress port is a member of the received VLAN ID in the bridge VLAN table. Should be used with frame-types to specify if the ingress traffic should be tagged or untagged. This property only has effect when vlan-filtering is set to yes.
- `last_member_interval` (String) If a port has fast-leave set to no and a bridge port receives a IGMP Leave message, then a IGMP Snooping enabled bridge will send a IGMP query to make sure that no devices has subscribed to a certain multicast stream on a bridge port.
- `last_member_query_count` (Number) How many times should last-member-interval pass until a IGMP Snooping bridge will stop forwarding a certain multicast stream. This property only has effect when igmp-snooping is set to yes.
- `max_hops` (Number) Bridge count which BPDU can pass in a MSTP enabled network in the same region before BPDU is being ignored. This property only has effect when protocol-mode is set to mstp.
- `max_message_age` (String) Changes the Max Age value in BPDU packets, which is transmitted by the root bridge. This property only has effect when protocol-mode is set to stp or rstp. Value: 6s..40s
- `membership_interval` (String) Amount of time after an entry in the Multicast Database (MDB) is removed if a IGMP membership report is not received on a certain port. This property only has effect when igmp-snooping is set to yes.
- `mld_version` (Number) Selects the MLD version. Version 2 adds support for source-specific multicast. This property only has effect when RouterOS IPv6 package is enabled and igmp-snooping is set to yes.
- `mtu` (String) The default bridge MTU value without any bridge ports added is 1500. The MTU value can be set manually, but it cannot exceed the bridge L2MTU or the lowest bridge port L2MTU. If a new bridge port is added with L2MTU which is smaller than the actual-mtu of the bridge (set by the mtu property), then manually set value will be ignored and the bridge will act as if mtu=auto is set.
- `multicast_querier` (Boolean) Multicast querier generates IGMP general membership queries to which all IGMP capable devices respond with an IGMP membership report, usually a PIM (multicast) router or IGMP proxy generates these queries. This property only has an effect when igmp-snooping is set to yes. Additionally, the igmp-snooping should be disabled/enabled after changing multicast-querier property.
- `multicast_router` (String) A multicast router port is a port where a multicast router or querier is connected. On this port, unregistered multicast streams and IGMP/MLD membership reports will be sent. This setting changes the state of the multicast router for a bridge interface itself. This property can be used to send IGMP/MLD membership reports and multicast traffic to the bridge interface for further multicast routing or proxying. This property only has an effect when igmp-snooping is set to yes.
- `priority` (String) Bridge priority, used by STP to determine root bridge, used by MSTP to determine CIST and IST regional root bridge. This property has no effect when protocol-mode is set to none.
- `protocol_mode` (String) Select Spanning tree protocol (STP) or Rapid spanning tree protocol (RSTP) to ensure a loop-free topology for any bridged LAN.
- `pvid` (Number) Port VLAN ID (pvid) specifies which VLAN the untagged ingress traffic is assigned to. It applies e.g. to frames sent from bridge IP and destined to a bridge port. This property only has effect when vlan-filtering is set to yes.
- `querier_interval` (String) Used to change the interval how often a bridge checks if it is the active multicast querier. This property only has effect when igmp-snooping and multicast-querier is set to yes.
- `query_interval` (String) Used to change the interval how often IGMP general membership queries are sent out. This property only has effect when igmp-snooping and multicast-querier is set to yes.
- `query_response_interval` (String) Interval in which a IGMP capable device must reply to a IGMP query with a IGMP membership report. This property only has effect when igmp-snooping and multicast-querier is set to yes.
- `region_name` (String) MSTP region name. This property only has effect when protocol-mode is set to mstp.
- `region_revision` (Number) MSTP configuration revision number. This property only has effect when protocol-mode is set to mstp.
- `startup_query_count` (Number) Specifies how many times must startup-query-interval pass until the bridge starts sending out IGMP general membership queries periodically. This property only has effect when igmp-snooping and multicast-querier is set to yes.
- `startup_query_interval` (String) Used to change the amount of time after a bridge starts sending out IGMP general membership queries after the bridge is enabled. This property only has effect when igmp-snooping and multicast-querier is set to yes.
- `transmit_hold_count` (Number) The Transmit Hold Count used by the Port Transmit state machine to limit transmission rate.
- `vlan_filtering` (Boolean) Globally enables or disables VLAN functionality for bridge.

### Read-Only

- `actual_mtu` (Number)
- `id` (String) The ID of this resource.
- `l2mtu` (Number) Layer2 Maximum transmission unit. [See](https://wiki.mikrotik.com/wiki/Maximum_Transmission_Unit_on_RouterBoards).
- `mac_address` (String) Current mac address.
- `running` (Boolean)

## Import
Import is supported using the following syntax:
```shell
# Import with the name of the bridge in case of the example use bridge
terraform import routeros_interface_bridge.bridge bridge
```
