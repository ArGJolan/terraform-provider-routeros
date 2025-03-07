# routeros_interface_ethernet (Resource)


## Example Usage
```terraform
resource "routeros_interface_ethernet" "test" {
  factory_name = "sfp-sfpplus8"
  name         = "swtich-eth0"
  mtu          = 9000
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `factory_name` (String) The factory name of the identifier, serves as resource identifier. Determines which interface will be updated.
- `name` (String) Name of the ethernet interface.

### Optional

- `advertise` (String) Advertised speed and duplex modes for Ethernet interfaces over twisted pair, 
				only applies when auto-negotiation is enabled. Advertising higher speeds than 
				the actual interface supported speed will have no effect, multiple options are allowed.
- `arp` (String) Address Resolution Protocol mode:
	* disabled - the interface will not use ARP
	* enabled - the interface will use ARP
	* local-proxy-arp - the router performs proxy ARP on the interface and sends replies to the same interface
	* proxy-arp - the router performs proxy ARP on the interface and sends replies to other interfaces
	* reply-only - the interface will only reply to requests originated from matching IP address/MAC address combinations which are entered as static entries in the ARP table. No dynamic entries will be automatically stored in the ARP table. Therefore for communications to be successful, a valid static entry must already exist.
- `arp_timeout` (String) ARP timeout is time how long ARP record is kept in ARP table after no packets are received from IP. Value auto equals to the value of arp-timeout in IP/Settings, default is 30s. Can use postfix ms, s, M, h, d for milliseconds, seconds, minutes, hours or days. If no postfix is set then seconds (s) is used.
- `auto_negotiation` (Boolean) When enabled, the interface "advertises" its maximum capabilities to achieve the best connection possible.
					Note1: Auto-negotiation should not be disabled on one end only, otherwise Ethernet Interfaces may not work properly.
					Note2: Gigabit Ethernet and NBASE-T Ethernet links cannot work with auto-negotiation disabled.
- `bandwidth` (String) Sets max rx/tx bandwidth in kbps that will be handled by an interface. TX limit is supported on all Atheros switch-chip ports. 
				RX limit is supported only on Atheros8327/QCA8337 switch-chip ports.
- `cable_settings` (String) Changes the cable length setting (only applicable to NS DP83815/6 cards)
- `combo_mode` (String) When auto mode is selected, the port that was first connected will establish the link. In case this link fails, the other port will try to establish a new link. If both ports are connected at the same time (e.g. after reboot), 
				the priority will be the SFP/SFP+ port. When sfp mode is selected, the interface will only work through SFP/SFP+ cage.
				When copper mode is selected, the interface will only work through RJ45 Ethernet port.
- `comment` (String)
- `disable_running_check` (Boolean) Disable running check. If this value is set to 'no', the router automatically detects whether the NIC is connected with a device in the network or not.
			Default value is 'yes' because older NICs do not support it. (only applicable to x86)
- `disabled` (Boolean)
- `full_duplex` (Boolean) Defines whether the transmission of data appears in two directions simultaneously, only applies when auto-negotiation is disabled.
- `l2mtu` (Number) Layer2 Maximum transmission unit. [See](https://wiki.mikrotik.com/wiki/Maximum_Transmission_Unit_on_RouterBoards).
- `loop_protect` (String)
- `loop_protect_disable_time` (String)
- `loop_protect_send_interval` (String)
- `mac_address` (String) Media Access Control number of an interface.
- `mdix_enable` (Boolean) Whether the MDI/X auto cross over cable correction feature is enabled for the port (Hardware specific, e.g. ether1 on RB500 can be set to yes/no. Fixed to 'yes' on other hardware.)
- `mtu` (Number) Layer3 Maximum transmission unit
- `poe_out` (String) PoE settings: (https://wiki.mikrotik.com/wiki/Manual:PoE-Out)
- `poe_priority` (Number) PoE settings: (https://wiki.mikrotik.com/wiki/Manual:PoE-Out)
- `rx_flow_control` (String) When set to on, the port will process received pause frames and suspend transmission if required.
					auto is the same as on except when auto-negotiation=yes flow control status is resolved by taking into account what other end advertises.
- `sfp_rate_select` (String) Allows to control rate select pin for SFP ports. Values: high | low
- `sfp_shutdown_temperature` (Number) The temperature in Celsius at which the interface will be temporarily turned off due to too high detected SFP module temperature (introduced v6.48).The default value for SFP/SFP+/SFP28 interfaces is 95, and for QSFP+/QSFP28 interfaces 80 (introduced v7.6).
- `speed` (String) Sets interface data transmission speed which takes effect only when auto-negotiation is disabled.
- `tx_flow_control` (String) When set to on, the port will generate pause frames to the upstream device to temporarily stop the packet transmission. 
					Pause frames are only generated when some routers output interface is congested and packets cannot be transmitted anymore. 
					Auto is the same as on except when auto-negotiation=yes flow control status is resolved by taking into account what other end advertises.

### Read-Only

- `default_name` (String) The default name for an interface.
- `driver_rx_byte` (Number) Total count of received bytes on device CPU
- `driver_rx_packet` (Number) Total count of received packets on device CPU
- `driver_tx_byte` (Number) Total count of transmitted packets by device CPU
- `driver_tx_packet` (Number) Total count of transmitted packets by device CPU
- `id` (String) The ID of this resource.
- `loop_protect_status` (String)
- `orig_mac_address` (String) Original Media Access Control number of an interface. (read only)
- `running` (Boolean) Whether interface is running. Note that some interface does not have running check and they are always reported as "running"
- `rx_broadcast` (Number) Total count of received broadcast frames.
- `rx_bytes` (Number) Total count of received bytes.
- `rx_error_events` (Number) Total count of received frames with active error event
- `rx_fcs_error` (Number) Total count of received frames with incorrect checksum
- `rx_fragment` (Number) Total count of received fragmented frames (not related to IP fragmentation)
- `rx_jabber` (Number) Total count of received jabbed packets - a packet that is transmitted longer than the maximum packet length
- `rx_multicast` (Number) Total count of received multicast frames.
- `rx_overflow` (Number) Total count of received overflowed frames, can be caused when device resources are insufficient to receive a certain frame
- `rx_packet` (Number) Total count of received packets.
- `rx_pause` (Number) Total count of received pause frames
- `rx_too_long` (Number) Total count of received frames that were larger than the maximum supported frame size by the network device, see the max-l2mtu property
- `rx_too_short` (Number) Total count of received frame shorter than the minimum 64 bytes
- `rx_unicast` (Number) Total count of received unicast frames
- `slave` (Boolean) Whether interface is configured as a slave of another interface (for example Bonding)
- `switch` (String) ID to which switch chip interface belongs to.
- `tx_broadcast` (Number) Total count of transmitted broadcast frames.
- `tx_bytes` (Number) Total count of transmitted bytes.
- `tx_collision` (Number) Total count of transmitted frames that made collisions
- `tx_drop` (Number) Total count of transmitted frames that were dropped due to already full output queue
- `tx_late_collision` (Number) Total count of transmitted frames that made collision after being already halfway transmitted
- `tx_multicast` (Number) Total count of transmitted multicast frames.
- `tx_packet` (Number) Total count of transmitted packets.
- `tx_pause` (Number) Total count of transmitted pause frames.
- `tx_rx_1024_max` (Number) Total count of transmitted and received 1024 or above byte frames
- `tx_rx_128_255` (Number) Total count of transmitted and received 128 to 255 byte frames
- `tx_rx_256_511` (Number) Total count of transmitted and received 256 to 511 byte frames
- `tx_rx_512_1023` (Number) Total count of transmitted and received 512 to 1024 byte frames
- `tx_rx_64` (Number) Total count of transmitted and received 64 byte frames
- `tx_rx_65_127` (Number) Total count of transmitted and received 64 to 127 byte frames
- `tx_underrun` (Number) Total count of transmitted underrun packets
- `tx_unicast` (Number) Total count of transmitted unicast frames.

## Import
Import is supported using the following syntax:
```shell
#The ID can be found via API or the terminal
#The command for the terminal is -> :put [/interface/ethernet get [print show-ids]]
terraform import routeros_interface_ethernet.test "*0"
```
