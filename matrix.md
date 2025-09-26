```html
nano /etc/matrix-synapse/homeserver.yaml
```
```html
server_name: "matrix.example.com"
pid_file: "/var/run/matrix-synapse.pid"
listeners:
  - port: 8008
    tls: false
    type: http
    x_forwarded: true
    bind_addresses: ['127.0.0.1']
    resources:
      - names: [client, federation]
        compress: false
database:
  name: psycopg2
  txn_limit: 10000
  args:
    user: synapse_user
    password: 123
    database: synapse_db
    host: 127.0.0.1
    port: 5432
    cp_min: 1
    cp_max: 25
log_config: "/etc/matrix-synapse/log.yaml"
media_store_path: "/var/lib/matrix-synapse/media_store"
signing_key_path: "/etc/matrix-synapse/homeserver.signing.key"
trusted_key_servers:
  - server_name: "matrix.org"
suppress_key_server_warning: true
enable_registration: false
registration_shared_secret: "12324"


registration/Shared Secret:
```html
nano /etc/matrix-synapse/conf.d/registration.yaml
```
```html
enable_registration: false
registration_shared_secret: "1234"
```

```html
chmod 600 /etc/matrix-synapse/conf.d/registration.yaml
chown matrix-synapse:matrix-synapse /etc/matrix-synapse/conf.d/registration.yaml
```

```html
systemctl restart matrix-synapse
systemctl status matrix-synapse
```

create Admin user
```html
register_new_matrix_user -c /etc/matrix-synapse/homeserver.yaml http://localhost:8008
```


