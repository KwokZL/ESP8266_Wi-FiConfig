<div align='center'>
  <img src='./docs/imgs/logo.png' style='width:200px'/>
  <h1>ESP8266_Wi-FiConfig</h1>
  <p>Connect Wi-Fi to ESP8266.</p>
  <a href='./docs/cn_zh.md'>简体中文</a>
</div>



## Introduction

This project is a Wi-Fi connection utility written for the ESP8266.

> Feel free to submit Issues and PRs to improve the project together.

## Developers

### Code Section

Modify and add your own logic based on the comments. You can also customize the HTML/CSS interface.

#### Customizable Sections and Notes

##### Configure Wi-Fi Name

The default is `Device Connect`, which you can modify.

> Note: The Wi-Fi name has a length limit. Exceeding it will cause errors.

##### Header Logo

Convert your image to Base64 and replace the corresponding Base64 field in the code.

##### HTML and CSS

You can customize the interface style and design your own provisioning page.

> Note: The logo is loaded via JS code. Ensure the element ID matches the one in the JS code. See details below.

#### Available APIs for the Provisioning Interface

##### Get Available Wi-Fi List

Request (GET): `http://192.168.4.1/WiFiList`

Response: Wi-Fi names wrapped in `<option>` and `</option>`

##### Connect to Wi-Fi

Request (GET): `http://192.168.4.1/connectWifi`

| Field    | Meaning           |
| :------- | :---------------- |
| ssid     | Target Wi-Fi name |
| password | Wi-Fi password    |

##### Get Logo

Request (GET): `http://192.168.4.1/img1`

> Note: This returns a JS code snippet, not the Base64-encoded image. If customizing HTML, refer to the example HTML and modify the corresponding element ID.

##### Get CSS

Request (GET): `http://192.168.4.1/css`

## Users

After powering on, the device will attempt to connect to the last saved Wi-Fi within 10 seconds. If it fails, the provisioning mode will activate automatically.

> The 10-second timeout can be adjusted in the code.

### Steps

1. Use a phone, computer, or other device to connect to the Wi-Fi named `Device Connect`.

2. After connecting, the configuration page will open automatically.

   > If it doesn’t, manually visit `http://192.168.4.1/` in a browser.

3. Follow the prompts to select a Wi-Fi network and enter the password.

4. After clicking "Connect," the webpage will close, and the device will reboot. If it still fails to connect within 10 seconds, repeat the steps.

   > Note: The device does not wait for a successful connection before exiting the provisioning page. Regardless of success (or password correctness), it will reboot and only attempt to connect within the 10-second window.