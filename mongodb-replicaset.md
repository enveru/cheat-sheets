# MongoDB Replica Set with SSL

## Create Root CA key and certificate

1.  Create Root CA key.

        openssl genrsa -aes256 -out rootCA.key 4096

2.  Create Root CA certificate.

        openssl req -new -x509 -sha256 -days 3650 -key rootCA.key -out rootCA.pem

## Create first instance key and certificate

1.  Create first instance key.

        openssl genrsa -out mongo0.key 4096

2.  Create first instance certificate signing request.

        openssl req -new -sha256 -key mongo0.key -out mongo0.csr

3.  Create extfile to configure signing request.

        echo "subjectAltName=DNS:mongo0.enveru.com,IP.1:10.5.0.5,IP.2:127.0.0.1" >> extfile.cnf

4.  Sign request with Root CA key and certificate.

        openssl x509 -req -sha256 -days 3650 -in mongo0.csr -CA rootCA.pem -CAkey rootCA.key -out mongo0.crt -extfile extfile.cnf -CAcreateserial

5.  Create pem file.

        cat mongo0.key mongo0.crt > mongo0.pem

6.  Test certificate.

        openssl verify -CAfile rootCA.pem -verbose mongo1.pem

## Create second instance key and certificate

1.  Create second instance key.

        openssl genrsa -out mongo1.key 4096

2.  Create second instance certificate signing request.

        openssl req -new -sha256 -key mongo1.key -out mongo1.csr

3.  Create extfile to configure signing request.

        echo "subjectAltName=DNS:mongo1.enveru.com,IP.1:10.5.0.5,IP.2:127.0.0.1" >> extfile.cnf

4.  Sign request with Root CA key and certificate.

        openssl x509 -req -sha256 -days 3650 -in mongo1.csr -CA rootCA.pem -CAkey rootCA.key -out mongo1.crt -extfile extfile.cnf -CAcreateserial

5.  Create pem file.

        cat mongo1.key mongo1.crt > mongo1.pem

6.  Test certificate.

        openssl verify -CAfile rootCA.pem -verbose mongo1.pem

## Create third instance key and certificate

1.  Create third instance key.

        openssl genrsa -out mongo2.key 4096

2.  Create third instance certificate signing request.

        openssl req -new -sha256 -key mongo2.key -out mongo2.csr

3.  Create extfile to configure signing request.

        echo "subjectAltName=DNS:mongo2.enveru.com,IP.1:10.5.0.5,IP.2:127.0.0.1" >> extfile.cnf

4.  Sign request with Root CA key and certificate.

        openssl x509 -req -sha256 -days 3650 -in mongo2.csr -CA rootCA.pem -CAkey rootCA.key -out mongo2.crt -extfile extfile.cnf -CAcreateserial

5.  Create pem file.

        cat mongo2.key mongo2.crt > mongo2.pem

6.  Test certificate.

        openssl verify -CAfile rootCA.pem -verbose mongo2.pem

## Create second instance key and certificate

1.  Create first instance key.

        openssl genrsa -out mongo1.key 4096

2.  Create first instance certificate signing request.

        openssl req -new -sha256 -key mongo1.key -out mongo1.csr

3.  Create extfile to configure signing request.

        echo "subjectAltName=DNS:mongo1.enveru.com,IP.1:10.5.0.5,IP.2:127.0.0.1" >> extfile.cnf

4.  Sign request with Root CA key and certificate.

        openssl x509 -req -sha256 -days 3650 -in mongo1.csr -CA rootCA.pem -CAkey rootCA.key -out mongo1.crt -extfile extfile.cnf -CAcreateserial

5.  Create pem file.

        cat mongo1.key mongo1.crt > mongo1.pem

6.  Test certificate.

        openssl verify -CAfile rootCA.pem -verbose mongo1.pem

## Create client key and certificate

1.  Create client key.

        openssl genrsa -out client.key 4096

2.  Create client certificate signing request.

        openssl req -new -sha256 -key client.key -out client.csr

3.  Create extfile to configure signing request.

        echo "subjectAltName=DNS:*.enveru.com,IP.1:10.5.0.5,IP.2:127.0.0.1" >> extfile.cnf

4.  Sign request with Root CA key and certificate.

        openssl x509 -req -sha256 -days 3650 -in client.csr -CA rootCA.pem -CAkey rootCA.key -out client.crt -extfile extfile.cnf -CAcreateserial

5.  Create pem file.

        cat client.key client.crt > client.pem

6.  Test certificate.

        openssl verify -CAfile rootCA.pem -verbose client.pem
