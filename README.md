# SMS-Retriever-API

## 1 - Get Certificate From Google App Signing
- Go to Google Play Console
- Select your app
- Go to Release Management > App Signing
- Download Certificate deployment_cert.der
### Example:
<img width="1145" alt="Screenshot 2024-05-23 at 5 21 10 PM" src="https://github.com/ahmedsaleh210/SMS-Retriever-API/assets/96204940/e4228315-98dd-4739-b67e-0a06c4ede34d">



## 2 -  Import the app signing certificate into a temporary key store

```shell
keytool -importcert -file deployment_cert.der -keystore temporary.keystore -alias PlayDeploymentCert
```


## 3 -  Generate the hash string
- Download this python script https://github.com/funambol/android-sms-hash-generator

- Run the script with the following command
```shell
python3 smshash.py temporary.keystore PlayDeploymentCert 12345678 com.example.myapp
```
- Replace PlayDeploymentCert with the alias you used in step 2 and com.example.myapp with your app package name and 12345678 with your keystore password
