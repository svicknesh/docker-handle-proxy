# Handle Proxy Composer

Docker compose file for deploying your very own Handle Proxy Server via Jetty.

## Notes

If you discover any typos or errors in this README.md, create an *ISSUE* with the relevant fix and I will make the changes accordingly. If you have any suggestions or improvements, please do the same.

## Pre-requisites

- Docker v17.05 or above.
- Docker compose v1.17.0 or above.

## Deploying docker instance

**NOTE**: The proxy does not need to be run as the `root` user. It is recommended to run it as a normal user who has permission to manage Docker instances.

1. Clone this repository to a folder of your choice and switch to that directory.
2. Start the Docker instance with Docker Compose like the following
```bash
docker-compose up -d
```

## Quick deployment

```bash
git clone https://github.com/svicknesh/docker-handle-lhs docker-handle-proxy
cd docker-handle-proxy
docker-compose up -d
```

## Accessing the Handle Proxy

The Handle Proxy is accessible at `http://<ip address>:8080/hdlproxy`. To make the proxy reachable via standard HTTP port 80, but you don't want to tinker with the configuration, just do the following

```bash
iptables -t nat -A PREROUTING -i _INTERFACE_ -p tcp --dport 80 -j DNAT --to-destination :8080
```
where **_INTERFACE_** is your Linux network interface.

## License

Feel free to use this as you see fit. It does not come with any warranty, implied or otherwise.


