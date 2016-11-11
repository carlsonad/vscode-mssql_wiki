# OpenSSL Configuration (Mac Only)
For macOS, you will need to install OpenSSL which is a pre-requiste for DotNet Core that mssql extention uses. Follow the 'install pre-requisite' steps in [DotNet Core instruction page](https://www.microsoft.com/net/core#macos).
Or, simply run the following commands in your macOS Terminal.

```bash
brew update
brew install openssl
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```