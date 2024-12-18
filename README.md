
# KPAProxy

**Reverse Proxy:** It also distributes traffic. However, it is primarily concerned with limiting and safeguarding server access or hiding your Server IP Address.

**Load Balancer:** Concerned with distributing traffic/requests. Prevent bottlenecks, maximize throughput, and optimize resource consumption.

**shMonitor or Server Health Monitor:** continuously checks the server's health, then removes it from the load balancer list in real-time if it becomes offline. Gracefully.

I am familiar with reverse proxies and network load balancers available in the market, such as those offered by AWS, Azure, and Google. However, some of these options were expensive and did not meet my needs.

That's why I created my version. I initially tested it for my project, and after a few days, I implemented it in our company. We have used it for years, and everything has performed as expected.

I no longer worry about server downtime because I have a load balancer and a server health monitor. I receive email and SMS notifications if any of my servers go down.

Additionally, I can check the server's health in real time and manage my load balancer anytime.

> I'd like to let you know that I've decided to turn off email notifications to enhance my focus and productivity.

## How to use it?

Download all files and save them to your preferred folder location.

**single-website** - Only use a single website if you use one module or site. No other websites will be proxied within that domain.

**multiple websites** — Use multiple websites only when managing several sites under one domain to maximize your impact and streamline your efforts.

Then, open IIS, Site -> Add Website -> point to the folder location. 

Then, bind the IP with a Port or use your Domain/Hostname.

> Please remember to set the permissions.

> Note: Tested on Windows 10/11 and Windows Server 2016/2019/2022. However, you can still add your server to the load balancer list/config, even if your website/app is from Linux/Nginx/Apache. Or run it using NPM/Node.

> **Available soon for Linux**

## Prerequisite

You must download and install the dotnet runtime. See the download link below:

[Download .Net 8 runtime (Hosting Bundle)](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-8.0.1-windows-hosting-bundle-installer "Dotnet 8")

# shMonitor

The **shMonitor** is an essential server health monitoring solution that ensures optimal performance. It continuously checks the status of your servers, and if any of them go down, it swiftly updates the load balancer list, preventing downtime and maintaining reliability.

## How to use it?

Before you run the **(shMonitor.exe)**, you must set your **(config.json)**. Enter your server IP addresses. See the sample below:

## Sample config.json

```
{
    "bind_ip": "0.0.0.0",
    "port": 21000,
    "channel": "ANY-STRING-UPDATE-ME",
    "error_notify": {
        "emails": "talkme@mail.kpa.ph",
        "mobiles": "639605614295"
    },
    "hostname": "sample.com",
    "cache_root": "C:/KPA-rpNlb",
    "servers": [
        {
            "name" : "my-website",
            "health_check_time": 3,
            "addresses": [
                {
                    "server_name": "my-localhost-a",
                    "server_location": "homelab-house",
                    "server_ip_address": "127.0.0.1",
                    "server_hostname": "http://127.0.0.1:8000",
                    "server_health_check": "http://127.0.0.1:8000/health"
                },
                {
                    "server_name": "my-localhost-b",
                    "server_location": "homelab-office",
                    "server_ip_address": "127.0.0.1",
                    "server_hostname": "http://127.0.0.1:9000",
                    "server_health_check": "http://127.0.0.1:9000/health"
                },
                {*** You can add more here. Remove this when you use it. ***}
            ]
        }
    ]
}
```

- **bind_ip** and **port** - for web access
- **channel** - For socket channel, any string as long as it is unique
- **error_notify** - For email and SMS notifications, if something goes wrong with the servers, this is not working now.
- **hostname** - Your domain
- **cache_root** - Folder for cache
- **servers** - For all servers to be load-balanced
    - **name** - any name as long as it is unique
    - **health_check_time** - default 3 seconds
    - **addresses** -
        - **server_name** - server name
        - **server_location** - server location
        - **server_ip_address** - server IP
        - **server_hostname** - HTTP and IP Address with Port only
        - **server_health_check** - http or https | You can create any path or any.html / *.extention. Be sure that the HTTP response is 200 code.

# Contact me

- Email: talkme@mail.kpa.ph
- Mobile#: +63 960 561 4295

# Donate

GCash / Maya: +63 960 561 4295

[Paypal](https://paypal.me/kpa21 "Paypal")
