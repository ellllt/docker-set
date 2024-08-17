# SSLでドメインアクセス可能なLAMP環境

## SSL証明書の設定

```
sudo apt update
sudo apt install mkcert
mkcert -install
cd local-proxy/certs/
mkcert "*.local.localhost"
mv _wildcard.local.localhost.pem _wildcard.local.localhost.crt
mv _wildcard.local.localhost-key.pem _wildcard.local.localhost.key
```

## ドメインを増やす場合

myappディレクトリを複製する
