# ESP32 Cellular AWS IoT Platform
The Buildstorm platform simplifies the integration of AWS IoT core features onto ESP32 Hardware, from basic IoT functionalities to advanced features like OTA updates and provisioning.

The architecture is based on the core IDF APIs, complemented by a C++ wrapper tailored for application use, guaranteeing non-blocking operation of all APIs. Each user action, including HTTP requests, MQTT publishing, Shadow updates, and OTA, is logged as an event and seamlessly managed in the background. To maintain this seamless operation, the platform effectively runs a system task.

This establishes a robust foundation for your upcoming IoT project.

Supported features:

1. MQTT pub/sub
2. Shadow updates
3. Jobs
4. Web OTA using AWS jobs and S3 bucket
5. Local webserver OTA
6. Provision by claim
7. BLE Device Provisioning
8. Wifi and Cellular co-existence

## Solution
1. [Cellular AWS IoT Solution](https://buildstorm.com/solutions/esp32-cellular-aws-iot/)

## Reference
1. [ESP32 – IDF: AWS IoT Device Provision](https://buildstorm.com/blog/esp32-idf-aws-iot-device-provision/)
2. [ESP32 AWS-IOT OTA library on ESP-IDF](https://buildstorm.com/blog/esp32-aws-iot-ota-library-on-esp-idf/)

## Requirements
1. This library uses esp-idf v5.2.0

---

## Example Setup
1. Follow [this article](https://buildstorm.com/blog/aws_iot_provision_by_claim/) to setup AWS and generate provisioning certificates.
2. Same certificates will be used for all examples
3. Copy the generated claim certificates to `examples\_Certificates\claimCerts` folder and rename them as follows
   1. `aws-root-ca.pem`
   2. `claim-certificate.pem`
   3. `claim-private.pem.key`
3. Copy the generated thing certificates to `examples\_Certificates\thingCerts` folder and rename them as follows
   1. `aws-root-ca.pem`
   2. `thing-certificate.pem`
   3. `thing-private.pem.key`
4. Use the repsective sdkconfig files for esp32, esp32s3. The partions settings is already taken care in the sdkconfigs.
5. Update the following WiFi and AWS parameters in `app_config.h` of the example
```
#define TEST_WIFI_SSID     "YOUR WIFI SSID"
#define TEST_WIFI_PASSWORD "YOUR WIFI PWD"

#define AWS_IOT_MQTT_HOST "YOUR AWS HOST"
#define AWS_IOT_MQTT_PORT  8883
#define AWS_PROVISION_TEMPLATE_NAME "YOUR PROVISION TEMPLATE"

#define MODEM_POWERKEY_GPIO_PIN 5
#define MODEM_RESETKEY_GPIO_PIN 4
#define MODEM_RX_UART_PIN 16
#define MODEM_TX_UART_PIN 17
#define MODEM_UART_NUM 2

#define APN "airtelgprs.com"
#define USERID ""
#define PASSWORD ""
```

---

## Soc Compatibility

| Name     | BLE       | OTA       |
| -------- | --------- | --------- |
| ESP32    | Supported | Supported |
| ESP32 S3 | Supported | Supported |



