Registrations have been disabled on this home server.
Cause: In the Synapse configuration file
/etc/matrix-synapse/homeserver.yaml <br>
By default it says:
enable_registration: false
systemctl restart matrix-synapse
If the server is public, any external user can register.<br>
Register only with Shared Secret (more secure)
enable_registration: false
registration_shared_secret: "secretpw"

bash: register_new_matrix_user -c /etc/matrix-synapse/homeserver.yaml http://localhost:8008


