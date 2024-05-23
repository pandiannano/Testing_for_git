from hardware import *
uart1 = UART(1, baudrate=115200, bits=8, parity=None, stop=1, tx=17, rx=18)
from unit import CATMUnit
catm_0 = CATMUnit(port=(18,17))

**status**
>> check if modem is ready (return true or false)
	catm_0.check_modem_is_ready()

>> get identification(IMEI) number(return string)
	nbiot_0.get_imei_number()

>> get signal strength (return int)
	catm_0.get_signal_strength()
	
>> get model identification (return string)
	catm_0.get_model_identification()
	
>> get gprs network status (return int)
	catm_0.get_gprs_network_status()
	
>> get show pdp address cid[1](1~2) (return string)
	catm_0.get_show_pdp_address(1)
	
>> get selected operator (return int)
	catm_0.get_selected_operator()

>> get preferred mode selection (return int)
	catm_0.get_mode_selection()
		
>> get APP Network Activated pdp id[0](0~3)
	catm_0.get_network_activated(0)
	
>> get network ip pdp id[0](0~3) (return string)
	catm_0.get_network_ip(0)	
	
**control**
>> set AT command debug print[enable]
	enable = True
	disable = False
	catm_0.modem_debug = True
	
>> set echo command mode[OFF]
	OFF = 0
	ON = 1
	catm_0.set_command_echo_mode(0)

>> set gprs network state[ENABLE]
	ENABLE=1
	DISABLE=0
	catm_0.set_gprs_network_state(1)
			
>> set define PDP context apn['CMNET']
	catm_0.set_pdp_context('CMNET')	

>> set preferred mode selection[CAT-M & NB]
	CAT-M = 1
	NB-IOT = 2
	CAT-M & NB = 3
	catm_0.set_mode_selection(3)

>> set APP network active PDP id[0](0~3) action [ACTIVE]
	ACTIVE = 1
	DEACTIVE = 0
	catm_0.set_network_active(0,1)


**mqtt**
>> mqtt server connect 
		server['mqtt.m5stack.com']
		port[1883]
		client id['']
		username['']
		password['']
		keepalive[120]
	catm_0.mqtt_server_connect('mqtt.m5stack.com', 1883, '', '', '', 120)

>> mqtt server disconnect()
	catm_0.mqtt_server_disconnect()

def catm_mqtt_cb_func1(mq_topic, mq_payload):
  global catm_topic, catm_msg
  catm_topic = catm_mq_topic
  catm_msg = catm_mq_payload
  pass

>> mqtt subscribe topic[''] Qos[0](0~2)
	catm_0.mqtt_subscribe_topic('', catm_mqtt_cb_func1, 0)

>> mqtt unsubscribe topic['']
	catm_0.mqtt_unsubscribe_topic('')

>> mqtt publish topic[''] payload[''] Qos[0](0~2)
	catm_0.mqtt_publish_topic('', '', 0)

>> mqtt polling loop
	catm_0.mqtt_polling_loop()
	
>> check mqtt server is connect(return int)
	catm_0.mqtt_server_is_connect()

**http**
>> http request
		method[GET]
		url['']
		header{}
		data{}
	GET = 1
	PUT = 2
	POST = 3
	catm_0.http_request(1, url, header, data)

>> http server connect
	catm_0.http_server_connect()

>> check http server is connect(return int)
	catm_0.is_http_server_connect()

>> http server disconnect
	catm_0.http_server_disconnect()

>> get response status code(return in)
	catm_0.response_code

>> get data content(return string)
	catm_0.data_content

