
* TOTP : One time Password algorithm ( RFC 6238 ) is an extension of
  the HMAC-based One-time Password algorithm( HOTP ) ( RFC 4226 ) that uses 
  at time-based moving factor instead of an event counter.

* Android Authenticator
   * advantage : Crossplatform library, app on all mainstream phone
   * Android autheicator Backend thats implements the functionality to validate a TOTP password,
   * java-totp
      * Credential generation 
      * Credential verification
      * QR-Code generation for the easy configuration of an account in the
        Google authenticator application
   * The QR Code can be obtained using a generated URL, which relies on the
     __Google Chart__ API to create a compliant QR code encoding the necessary iinformation
   * Google authenticator can use built-in camera of the cellular to take picture
     of the generated QR-Code and configure a new account using the information
     contained therein


* All the API members are published by the following interfaces and classes:
   * IGoogleAuthenticator 
      * main API interface
      * publish the library entry points
   * GoogleAuthenticatorKey
      * credentials container
      * mainly used when returning newly-created credentials
   * GoogleAuthenticatorQRGenerator
      * Helper class provides QR code generation using the Google Chart HTTP API
   * ICredentialRepository
         * method
            * createCredentials()
            * authorize( String secret , int verificationCode )
            * createCredentials( string userName )
            * authorizeUser( String username, int verificationCode )

      

