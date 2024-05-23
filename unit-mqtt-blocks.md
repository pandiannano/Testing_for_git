from unit import MQTTUnit
mqtt_0 = MQTTUnit(port=(18,17))

**status**
>> check if modem is ready (return true or false)
	mqtt_0.check_modem_is_ready()
	
>> get firmware version(return string)
	mqtt_0.get_firmware_version()

>> get device baudrate (return int)
	mqtt_0.get_baudrate()
	
>> get network connection status (return int)
	mqtt_0.get_network_status()
	
>> get network [IP] address (return string)
	IP = 0
	SUBNET = 1
	GATEWAY = 2
	DNS = 3
	mqtt_0.get_network_parameters(0)

>> get MAC address (return string)
	mqtt_0.get_mac_address()
		
>> get static[IP] address (return string)
	IP = 0
	SUBNET = 1
	GATEWAY = 2
	mqtt_0.get_static_ip(0)

>> get DHCP status (return int)
	IP = 0
	SUBNET = 1
	GATEWAY = 2
	mqtt_0.get_dhcp_status()	
	
**control**
>> set AT command debug print[enable]
	enable = True
	disable = False
	mqtt_0._debug = True

>> set DHCP state[enable]
	enable = 1
	disable = 0
	mqtt_0.set_dhcp_state(1)
	
>> set static IP["192.168.2.101"] SUBNET["255.255.255.0"] GATEWAY["192.168.2.1"]
	mqtt_0.set_static_ip("192.168.2.101", "255.255.255.0", "192.168.2.1")

**mqtt**
>> mqtt server connect 
		server['mqtt.m5stack.com']
		port[1883]
		client id['']
		username['']
		password['']
		keepalive[120]
	mqtt_0.set_mqtt_server_config('mqtt.m5stack.com', 1883, '', '', '', 120)

>> save current mqtt configure settings
	mqtt_0.save_current_config()

>> mqtt service start()
	mqtt_0.set_mqtt_service_start()

>> mqtt service stop()
	mqtt_0.set_mqtt_service_stop()

def mqtt_cb_func1(mq_topic, mq_payload):
  global _topic, _msg
  _topic = mq_topic
  _msg = mq_payload
  pass

>> mqtt subscribe serial no[1](1~4) topic[''] Qos[0](0~2)
	mqtt_0.set_mqtt_subscribe(1, '', 0, mqtt_cb_func1)

>> mqtt publish topic[''] payload[''] Qos[0](0~2)
	mqtt_0.set_mqtt_publish('', '', 0)

>> mqtt polling loop
	mqtt_0.mqtt_polling_loop()
	
>> get mqtt connection status (return int)
	mqtt_0.get_mqtt_status()


