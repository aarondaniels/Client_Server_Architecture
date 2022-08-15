# Authorization and Authentication
Authentication: Who are you? 
Auhorization: What are you allowed to do? 

# Open SSL

OpenSSL is a library used for communication and is used for encrypting and decrypting messages and files for security purposes.

OpenSSL works with private and public keys to encrypt and decrypt text using Terminal window commands.

The general syntax for any OpenSSL command is:

`$ openssl command [ command_options ] [ command_arguments ]`

To generate a private RSA key, you will need to use the command:

`$ openssl genrsa -out private.pem [bits]`

In the line above, the command genrsa instructs OpenSSL to create an RSA key named private.pem. Another extension often used to generate keys is .key. Finally, [bits] represents the number of bits you want to use for the key (typically 512).

If you want to generate a public key from a previous one you created, the syntax is:

`$ openssl rsa -in private.pem  -pubout > public.pem`

In the syntax above, the command rsa reads from the private key private.pem and outputs it to a publickey file named public.pem.

If you need to sign a document or a file with a private key, then you will need to use the following syntax. Note that the following syntax uses a cryptography function named sha1. However, others such as sha256, sha384, and sha512 do exist. Additionally, the example below uses a .txt file, but files with any type of extensions can be encrypted.

`$ openssl dgst -sha1 -sign public.pem -out sha1.sign your_document.txt`

Specifically, in the syntax above, you can simply embed the private key in the document your_document.txt by signing it using the signature sha1.sign.

To verify a public key together with a signature when decrypting a message, the syntax to use is:

`$ openssl dgst -sha1 -verify public.pem -signature sha1.sign your_document.txt`

After generating keys and verifying your signature, the next step is to encrypt a document. Following the steps above, this can be achieved in the following way:

`$ openssl rsautl -encrypt -pubin -inkey public.pem -ssl -in your_document.txt -out your_encrypted_document.txt`

In the syntax above, the rsautl command can be used to sign, verify, encrypt, and decrypt data by using the RSA algorithm. The argument -encrypt signifies to encrypt the input data by using an RSA public key. The argument -pubin signifies that the input file is an RSA public key. The argument -inkey denotes the name of the key file. Finally, the argument -ssl denotes what padding to use. The remainder of the command identifies the file to encrypt and names the encrypted file.

To decrypt a file using a key provided by another user, you will need to use the following syntax:

`$ openssl rsautl -decrypt -inkey user_public_key.pem -in user_document.txt -out user_decrypted_document.txt`

In the syntax above, the argument -decrypt signifies to decrypt the input data by using the RSA public key provided to you. The remainder of the command identifies the file to decrypt and names the decrypted file.

Of course, there are many different types of encryption and decryption methods that can be used dependent on needs. However, the RSA method is the most popular and simplest to use. Feel free to review the official OpenSSL Documentation (Links to an external site.) for further exploration.

# OAuth2
OAuth is an authorization protocol that describes how unrelated servers and services can safely allow authenticated access to their assets without actually using login credentials. OAuth was first created in 2010; the more recent and more popular version, OAuth2, was released in 2012.

The simplest example of how to use OAuth is when you want to log in to a website and it offers you the possibility of using other credentials from other websites. What happens in these cases is that you choose the website that will authenticate you, and it will communicate to the original website you are trying to access that your credentials are correct, thus granting you access.

In other words, OAuth helps a user accomplish something, such as logging on, between two unrelated websites.

The key detail to remember about OAuth is that it’s focus is on authorization, not authentication. Authentication is the process of a user providing a password to prove their identity. Authorization is the process of letting a subject access resources after successful authentication.

# What Is Okta?

Okta is a platform that enables multiple users (for example users working for the same company) to access various software with the same login. The main reason why organizations use Okta is to allow access to the cloud and services without using single authentications. This means easier access to software through a platform that is secure and reliable.

# API Token Management with Okta

“API tokens are used to authenticate requests to the Okta API just like HTTP cookies authenticate requests to the Okta Application with your browser. An API token is issued for a specific user and all requests with the token act on behalf of the user. API tokens are secrets and should be treated like passwords.

API tokens are generated with the permissions of the user that created the token. If a user’s permissions change, then so does that of the token. API tokens are valid for 30 days and automatically renew every time they are used with an API request. When a token has been inactive for more than 30 days, it is revoked and cannot be used again.

Tokens are also only valid if the user who created the token is also active. Tokens issued by deactivated users are rejected. If the user account is reactivated, the API token is accepted with no other action required.

With OAuth2 for Okta, you are able to interact with Okta APIs using scoped OAuth2 access tokens. Each access token enables you to perform specific actions on specific Okta APIs with ability controlled by which scopes the access token contains.

In summary, OAuth2 is an authorization protocol used for accessing services without specific login credentials for those services. Okta can be used in conjunction with OAuth2 to create API tokens that authenticate requests for users.