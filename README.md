# SMS-Retriever-API

## Step 1: Obtain Certificate From Google App Signing
- Navigate to the **Google Play Console**
- Choose your application
- Proceed to **Release Management > App Signing**
- Click on **Download Certificate** to get `deployment_cert.der`
### Example:
<img width="1145" alt="Screenshot 2024-05-23 at 5 21 10 PM" src="https://github.com/ahmedsaleh210/SMS-Retriever-API/assets/96204940/e4228315-98dd-4739-b67e-0a06c4ede34d">


## Step 2: Import the App Signing Certificate into a Temporary Key Store

Use the following shell command:

```shell
keytool -importcert -file deployment_cert.der -keystore temporary.keystore -alias PlayDeploymentCert
```

This command imports the certificate (`deployment_cert.der`) into a temporary key store (`temporary.keystore`) with an alias (`PlayDeploymentCert`).


## Step 3: Generate the Hash String

First, download the Python script from this link: [android-sms-hash-generator](https://github.com/funambol/android-sms-hash-generator)

Then, execute the script using the following command:

```shell
python3 smshash.py temporary.keystore PlayDeploymentCert 12345678 com.example.myapp
```

In this command, replace `PlayDeploymentCert` with the alias you used in step 2, `com.example.myapp` with your app package name, and `12345678` with your keystore password.
