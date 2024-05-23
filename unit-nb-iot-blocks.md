from unit import NBIOTUnit
nbiot_0 = NBIOTUnit(port=(18,17))

**status**
>> check if modem is ready (return true or false)
	nbiot_0.check_modem_is_ready()
	
>> get identification(IMEI) number(return string)
	nbiot_0.get_imei_number()

>> get signal strength (return int)
	nbiot_0.get_signal_strength()
	
>> get model identification (return string)
	nbiot_0.get_model_identification()
	
>> get gprs network status (return int)
	nbiot_0.get_gprs_network_status()
	
>> get show pdp address cid (return string)
	nbiot_0.get_show_pdp_address(1)

>> get pdp context status (return int)
	nbiot_0.get_pdp_context_status()
		
>> get pdp context network [IP] parameters (return string)
	IP = 1
	APN = 2
	nbiot_0.get_pdp_context_dynamic_parameters(1)	
	
**control**
>> set AT command debug print[enable]
	enable = True
	disable = False
	nbiot_0.modem_debug = True
	
>> set echo command mode[OFF]
	OFF = 0
	ON = 1
	nbiot_0.set_command_echo_mode(0)

>> set gprs network state[ENABLE]
	ENABLE=1
	DISABLE=0
	nbiot_0.set_gprs_network_state(1)
			
>> set define PDP context apn['cmnbiot']
	nbiot_0.set_pdp_context_apn('cmnbiot')	

>> set pdp context state[ACTIVATE]
	ACTIVATE = 1
	DEACTIVATE = 0
	nbiot_0.set_pdp_context(1)

**mqtt**
>> mqtt server connect 
		server['mqtt.m5stack.com']
		port[1883]
		client id['']
		username['']
		password['']
		keepalive[120]
	nbiot_0.mqtt_server_connect('mqtt.m5stack.com', 1883, '', '', '', 120)

>> mqtt server disconnect()
	nbiot_0.mqtt_server_disconnect()

def nbiot_mqtt_cb_func1(mq_topic, mq_payload):
  global nbiot_topic, nbiot_msg
  nbiot_topic = mq_topic
  nbiot_msg = mq_payload
  pass

>> mqtt subscribe topic[''] Qos[0](0~2)
	nbiot_0.mqtt_subscribe_topic('', nbiot_mqtt_cb_func1, 0)

>> mqtt unsubscribe topic['']
	nbiot_0.mqtt_unsubscribe_topic('')

>> mqtt publish topic[''] payload[''] Qos[0](0~2)
	nbiot_0.mqtt_publish_topic('', '', 0)

>> mqtt polling loop
	nbiot_0.mqtt_polling_loop()
	
>> check mqtt server is connect(return int)
	nbiot_0.mqtt_server_is_connect()

**http**
>> http request
		method[GET]
		url['']
		header{}
		data{}
	GET = 0
	POST = 1
	PUT = 2
	DELETE = 3
	nbiot_0.http_request(0, url, header, data)

>> http server connect
	nbiot_0.http_server_connect()

>> check http server is connect(return int)
	nbiot_0.is_http_server_connect()

>> http server disconnect
	nbiot_0.http_server_disconnect()

>> http server closed
	nbiot_0.http_server_destroy()

>> get http response status code(return int)
	nbiot_0.response_code

>> get http data content(return string)
	nbiot_0.data_content

