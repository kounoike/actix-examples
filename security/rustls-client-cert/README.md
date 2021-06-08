# Access Client Certificate (via Rustls)

## Usage

### Certificate

All the self-signed certificate are in the ./certs directory, including the CA certificate
generated by [`mkcert`] that was used to create the server and client certs.

### Server

```sh
cd examples/rustls-client-cert
cargo run
```

The server runs HTTP on port 8080 and HTTPS on port 8443.

### Providing Client Cert

Using [HTTPie]:
```sh
http https://127.0.0.1:8443/ --verify=certs/rootCA.pem --cert=certs/client-cert.pem --cert-key=certs/client-key.pem
```

Using [cURL]:
```sh
curl https://127.0.0.1:8443/ --cacert certs/rootCA.pem --cert certs/client-cert.pem --key certs/client-key.pem
```

[`mkcert`]: https://github.com/FiloSottile/mkcert
[cURL]: https://curl.haxx.se/
[HTTPie]: https://httpie.org/