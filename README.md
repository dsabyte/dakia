<!--
```text
_______
\  ___ `'.                    .          .--.
 ' |--.\  \                 .'|          |__|
 | |    \  '              .'  |          .--.
 | |     |  '     __     <    |          |  |     __
 | |     |  |  .:--.'.    |   | ____     |  |  .:--.'.
 | |     ' .' / |   \ |   |   | \ .'     |  | / |   \ |
 | |___.' /'  `" __ | |   |   |/  .      |  | `" __ | |
/_______.'/    .'.''| |   |    /\  \     |__|  .'.''| |
\_______|/    / /   | |_  |   |  \  \         / /   | |_
              \ \._,\ '/  '    \  \  \        \ \._,\ '/
               `--'  `"  '------'  '---'       `--'  `"
```
-->

<!-- canva logo url -> https://www.canva.com/design/DAGZAdY1d9c/YCHWZRD78H5j0CAWaaF6gw/edit -->

<!-- ![dakia logo](https://github.com/user-attachments/assets/7877c4bb-4358-4297-9213-e29d81550f99) -->

![dakia logo (1)](https://github.com/user-attachments/assets/44a908dd-a79c-4045-9e3e-b3125a5efdc5)

# Dakia is an API Gateway that’s Fully Programmable, Configurable, and Extensible!

**Dakia** is a powerful and flexible API Gateway designed for modern web applications.

## Features

> Work is in-progress

- **Fully Programmable**: Tailor the API Gateway to your specific needs with custom plugins and middleware in multiple languages.
- **Configurable**: Easily manage API configurations using various formats like YAML, JSON, and HTTP API calls.
- **Extensible**: Add new functionality with support for custom middleware and plugins, written in any programming language (Rust, Java, C++, etc.).
- **Zero Downtime Upgrades**: Perform upgrades and restarts without affecting the availability of your services.
- **Dynamic Middleware**: Add, remove, or modify middleware on the fly without disrupting service.
- **Request and Response Management**: Modify requests before they reach the upstream or read/write responses to meet your application's needs.
- **High-Performance**: Built on top of pingora which is battle-tested service with high traffic loads, serving more than **40** millions of requests per second.
- **Real-Time Configuration**: Modify your gateway configuration in real time with no downtime, using HTTP API calls.

Dakia ensures your services stay performant, reliable, and highly customizable, giving you full control.

## 📊 Progress Tracker

| Task            | Status      |
| --------------- | ----------- |
| Proxy           | Done ✅     |
| Load Balancer   | In-Progress |
| Caching         | Pending     |
| Rate Limiting   | Pending     |
| Plan Next Steps | Pending     |

## How to?

```yaml
daemon: true
error_log: "/var/log/dakia/error.log"
pid_file: "/var/run/dakia.pid"
upgrade_sock: "/var/run/dakia.sock"
user: "dakia_user"
group: "dakia_group"
threads: 4
work_stealing: true
grace_period_seconds: 60
graceful_shutdown_timeout_seconds: 30
upstream_keepalive_pool_size: 10
upstream_connect_offload_threadpools: 2
upstream_connect_offload_thread_per_pool: 5
upstream_debug_ssl_keylog: false
router_config:
  gate_ways:
    - listen:
        - host: "0.0.0.0"
          port: 8080
          sni: null
          tls: false
        - host: "0.0.0.0"
          port: 80
          sni: null
          tls: true
      hosts:
        - host: "w3worker.net"
      locations:
        - path: "/first"
          backend: "back2"
        - path: "*"
          backend: "back1"
      backends:
        - name: "back1"
          default: true
          upstreams:
            - inet_address:
                host: "0.0.0.0"
                port: 3000
              sni: null
              tls: false
        - name: "back2"
          default: false
          upstreams:
            - inet_address:
                host: "0.0.0.0"
                port: 3001
              sni: null
              tls: false
```
