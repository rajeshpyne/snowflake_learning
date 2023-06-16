Multi-Factor Authentication
=============================

- MFA is an additional layer of security, requiring the user to prove their identity not only with a 
    password but with an additional piece of information(or factor).

- MFA in Snowflake is powered by a service called `DUO Security`. You can install it in mobile as an app.

- MFA is enabled on a `per-user basis` & only via the UI

- Snowflake recommend that all users with the `ACCOUNTADMIN` role be required to use `MFA`.


* Federated Authentication or SSO also can be used for logging in Snowflake

Key Pair Authentication
-------------------------
1. Generate Key-Pair using OPENSSL  with 2048 bit RSA key pair( Public Key and Private Key )
2. Assign Public Key to Snowflake User
    `ALTER USER <user1> SET RSA_PUBLIC_KEY='<rsa_public_key>'`
    And `PrivateKey`  is kept safe locally by the user.
3. Configure Snowflake Cient
   - SnowSQL
   - Python Connector
   - Other driver connectors...

* `Key-Pair Rotation` 
  - This allows you to update the active public key.
  - It's enabled by allowing two active keys so you can swap them with no downtime.
  - The commands here show setting a second key and then unseating the now out-of-date first key.

    `ALTER USER <user> SET RSA_PUBLIC_KEY_2='<new_rsa_public_key2>';`
    `ALTER USER <user> UNSET RSA_PUBLIC_KEY`;

OAuth 
------

- Snowflake supports the OAuth2.0 protocol
- OAuth is an open-standard protocol that allows supported clients authorized access to Snowflake
    without sharing or storing user login credentials
    
    This allows something like a Tableau client to connect to Snowflake without having to maintain usernames and passwords.

- Snowflake offers two OAuth pathways:
    - Snowflake OAuth
    - External OAuth

SCIM (System for Cross-Domain Identity Management)
-----------------------------------------------------

SCIM can be used to manage users and groups (Snowflake roles) in cloud applications using  RESTFUL APIs.

SnowFlake ---APICALL (201)---> Microsoft
Snowflake <---CREATE USER----- Microsoft