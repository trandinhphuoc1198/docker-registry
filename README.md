# SERVER SIDE

0. Install Mkcert. Just curl and install binary. See [project][mkcert] for more instruction

1. Create CA

    ```bash
    mkcert -install
    ```

2. Copy CA cert into certs directory

    ```bash
    cp  $(mkcert -CAROOT)/rootCA.pem certs/ca.crt
    ```

3. Generate certificate

    ```bash
    mkcert -cert-file certs/registry.crt -key-file certs/registry.key localhost 192.168.1.1 tkg-bootstrap-registry.local
    ```
    
# CLIENT SIDE

1. Copy CA cert to docker folder
    ```
    cp ca.crt /etc/docker/certs.d/<my-registry.example.com:5000>/ca.crt
    ```
2. Restart docker service