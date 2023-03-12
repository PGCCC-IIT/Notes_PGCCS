---
### The title for the content.
title : "Shodan"
### If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle : "Shodan"
### The title of the page in menu will be prefixed by this HTML content
# pre : ""
### The title of the page in menu will be postfixed by this HTML content
# post : ""
### The description for the content.
description : "Use the power of OSINT."
### The datetime assigned to this page.
date : 2020-03-10T16:43:44+01:00
### Appears as the tail of the output URL. A value specified in front matter will override the segment of the URL based on the filename.
# slug : "social-media"
### Aliases can be used to create redirects to your page from other URLs.
# aliases : [""]
### Display name of this page modifier. If set, it will be displayed in the footer.
# LastModifierDisplayName : ""
### Email of this page modifier. If set with LastModifierDisplayName, it will be displayed in the footer
# LastModifierEmail : ""
### Table of content (toc) is enabled by default. Set this parameter to true to disable it.
# disableToc : true
### Set the page as a chapter, changing the way it's displayed
# chapter : true
### Hide a menu entry by setting this to true
# hidden : true
### If true, the content will not be rendered unless the --buildDrafts flag is passed to the hugo command.
# draft : true
### Used for ordering your content in lists. Lower weight gets higher precedence. So content with lower weight will come first.
### 0 does nothing !
weight : 0
### Used to tag content. By default this is inherited using cascading from _index.md files
### Only set of you want to overwrite these inherited values.
tags : ["Shodan"]
---

## Shodan

[Source](https://github.com/JavierOlmedo/shodan-filters/blob/master/README.md)

## General Filters
| **Name**           | **Description**                                                                                                                                                                                                            | **Type** |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| **after**          | Only show results after the given date (dd/mm/yyyy) string                                                                                                                                                                 | string   |
| **asn**            | Autonomous system number string                                                                                                                                                                                            | string   |
| **before**         | Only show results before the given date (dd/mm/yyyy) string                                                                                                                                                                | string   |
| **category**       | Available categories: ics, malware string                                                                                                                                                                                  | string   |
| **city**           | Name of the city string                                                                                                                                                                                                    | string   |
| **country**        | 2-letter country code string                                                                                                                                                                                               | string   |
| **geo**            | Accepts between 2 and 4 parameters. If 2 parameters: latitude,longitude. If 3 parameters: latitude,longitude,range. If 4 parameters: top left latitude, top left longitude, bottom right latitude, bottom right longitude. | string   |
| **hash**           | Hash of the data property integer                                                                                                                                                                                          | integer  |
| **has_ipv6**       | True/ False boolean                                                                                                                                                                                                        | boolean  |
| **has_screenshot** | True/ False boolean                                                                                                                                                                                                        | boolean  |
| **hostname**       | Full hostname for the device string                                                                                                                                                                                        | string   |
| **ip**             | Alias for net filter string                                                                                                                                                                                                | string   |
| **isp**            | ISP managing the netblock string                                                                                                                                                                                           | string   |
| **net**            | Network range in CIDR notation (ex. 199.4.1.0/24) string                                                                                                                                                                   | string   |
| **org**            | Organization assigned the netblock string                                                                                                                                                                                  | string   |
| **os**             | Operating system string                                                                                                                                                                                                    | string   |
| **port**           | Port number for the service integer                                                                                                                                                                                        | string   |
| **postal**         | Postal code (US-only) string                                                                                                                                                                                               | string   |
| **product**        | Name of the software/ product providing the banner string                                                                                                                                                                  | string   |
| **region**         | Name of the region/ state string                                                                                                                                                                                           | string   |
| **state**          | Alias for region string                                                                                                                                                                                                    | string   |
| **version**        | Version for the product string                                                                                                                                                                                             | string   |
| **vuln**           | CVE ID for a vulnerability string                                                                                                                                                                                          | string   |
## HTTP Filters
| **Name**                    | **Description**                                  | **Type** |
| --------------------------- | ------------------------------------------------ | -------- |
| **http.component**          | Name of web technology used on the website       | string   |
| **http.component_category** | Category of web components used on the   website | string   |
| **http.html**               | HTML of web banners                              | string   |
| **http.html_hash**          | Hash of the website HTML                         | integer  |
| **http.status**             | Response status code                             | integer  |
| **http.title**              | Title for the web banners website                | string   |

## NTP Filters
| **Name**         | **Description**                                                              | **Type** |
| ---------------- | ---------------------------------------------------------------------------- | -------- |
| **ntp.ip**       | IP addresses returned by monlist                                             | string   |
| **ntp.ip_count** | Number of IPs returned by initial monlist                                    | integer  |
| **ntp.more**     | True/ False; whether there are more IP addresses to be gathered from monlist | boolean  |
| **ntp.port**     | Port used by IP addresses in monlist                                         | integer  |

## SSL Filters
| **Name**                 | **Description**                                       | **Type**         |
| ------------------------ | ----------------------------------------------------- | ---------------- |
| **has_ssl**              | True / False                                          | boolean          |
| **ssl**                  | Search all SSL data                                   | string           |
| **ssl.alpn**             | Application layer protocols such as HTTP/2 ("h2")     | string           |
| **ssl.chain_count**      | Number of certificates in the chain                   | integer          |
| **ssl.version**          | Possible values: SSLv2, SSLv3, TLSv1,TLSv1.1, TLSv1.2 | string           |
| **ssl.cert.alg**         | Certificate algorithm                                 | string           |
| **ssl.cert.expired**     | True / False                                          | boolean          |
| **ssl.cert.extension**   | vNames of extensions in the certificate               | string           |
| **ssl.cert.serial**      | Serial number as an integer or hexadecimal string     | integer / string |
| **ssl.cert.pubkey.bits** | Number of bits in the public key                      | integer          |
| **ssl.cert.pubkey.type** | Public key type                                       | string           |
| **ssl.cipher.version**   | SSL version of the preferred cipher                   | string           |
| **ssl.cipher.bits**      | Number of bits in the preferred cipher                | integer          |
| **ssl.cipher.name**      | Name of the preferred cipher                          | string           |

## Telnet Filters
| **Name**          | **Description**                                             | **Type** |
| ----------------- | ----------------------------------------------------------- | -------- |
| **telnet.option** | Search all the options                                      | string   |
| **telnet.do**     | The server requests the client do support these options     | string   |
| **telnet.dont**   | The server requests the client to not support these options | string   |
| **telnet.will**   | The server supports these options                           | string   |
| **telnet.wont**   | The server doesnt support these options                     | string   |