Wir hätten auch den Cert-Manager konfigurieren können

Image unter: ~/Artikel/Docker/Dockerfile/apacheCertCGI

Aber so geht das für die Übung schneller 

Jetzt mal mit cfssl 

Das hier dient nur als Doku


~~~
cfssl gencert -initca ca.json | cfssljson -bare ca
~~~


~~~
cfssl gencert \
  -ca=ca.pem \
    -ca-key=ca-key.pem \
      -config=ca-config.json \
        -profile=web-servers \
          webhook-csr.json | cfssljson -bare check 
~~~

~~~
cfssl gencert \
  -ca=ca.pem \
    -ca-key=ca-key.pem \
      -config=ca-config.json \
        -profile=web-servers \
          webhook-csr.json | cfssljson -bare server
~~~
