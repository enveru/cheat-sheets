# MongoDB Replica Set with SSL

1.  Create Root CA key.

        openssl genrsa -aes256 -out rootCA.key 4096

2.  Create Root CA certificate.

        openssl req -new -x509 -sha256 -days 3650 -key rootCA.key -out rootCA.pem

3.  To see how you can add code snippets, see below:

        <h1>Some HTML code I'm proud of</h1>

        .proud-of-this-css {
        color: papayawhip;
        }

        const proudOfThisFunc = () => {
          console.log('🎉');
        };
