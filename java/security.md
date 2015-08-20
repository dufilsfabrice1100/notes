
# Goal of JCA 

* laisser l implementation a des fournisseurs
* extensible
* assurer l independance et garantir l interoperabilité 

# Fonctionalités de JCA 

* Algorithmes pour __Message digest__
* Algorithmes pour __Signature digitale__
* Cryptographie symétrique par __lot ou par flux__
* cryptographie asymetrique
* Password-based encryption __PBE__
* Elliptic Curve Cryptographie __ECC__
* Algorithmes pour Key agreement
* Generateur de Clés __KeyGenerator__
* Message Authentification Code __MAC__
* Generation de nombre pseudo aléatoire __SecureRandom__
* Stockage et Getion de Clés et certificats 

# Class de JCA 

## Clées 

* __Key__ :  Decrit les fonctionalités communes a toutes les clés opaques
* __PrivateKey__ : Clé privée
* __PublicKey__ : Clé publique


# Methodes generales de la class JCA 

* update() -> permet d ajouter des données à trainter en une seule ou plusieurs fois. 

      update( byte input )
      update( byte[] input )
      update( byte[] input, int offset, int len )



# Signature et Verfication 
 
Les objects de type __Signature__ possède un qui peut prendre trois valeurs : 

* UNINITIALIZED
* SIGN
* VERIFY

## Creation d une signature digitale

* Instancier un object de type __Signature__ 
* Initialiser l instance avec une clé privée. __initSign( PrivateKey key )__
* Les données sont fournies à l objet Signature pour créer la signature. 

## Effectuer une verification

* Instancier un object de type __Signature__ 
* Initialiser avec la clé publique __initVerify( PublicKey key )__
* Les données sont fournies a l objet Signature pour verification


