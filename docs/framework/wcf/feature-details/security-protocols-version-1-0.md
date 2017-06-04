---
title: "Protocoles de s&#233;curit&#233; version 1.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Protocoles de s&#233;curit&#233; version 1.0
Les protocoles Web Services Security fournissent des mécanismes de sécurité des services Web qui couvrent l'ensemble des exigences de sécurité de la messagerie de l'entreprise.  Cette section décrit dans le détail la version 1.0 de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] \(implémentée dans <xref:System.ServiceModel.Channels.SecurityBindingElement>\) pour les protocoles de sécurité des services Web suivants.  
  
|||  
|-|-|  
|Spécification\/Document|Link|  
|WSS : SOAP Message Security 1,0|http:\/\/docs.oasis\-open.org\/wss\/2004\/01\/oasis\-200401\-wss\-soap\-message\-security\-1.0.pdf|  
|WSS : Username Token Profile 1.0|http:\/\/docs.oasis\-open.org\/wss\/2004\/01\/oasis\-200401\-wss\-username\-token\-profile\-1.0.pdf|  
|WSS : X509 Token Profile 1,0|http:\/\/docs.oasis\-open.org\/wss\/2004\/01\/oasis\-200401\-wss\-x509\-token\-profile\-1.0.pdf|  
|WSS: SAML 1.1 Token Profile 1,0|http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.0.pdf|  
|WSS : SOAP Message Security 1.1|http:\/\/www.oasis\-open.org\/committees\/download.php\/16790\/wss\-v1.1\-spec\-os\-SOAPMessageSecurity.pdf|  
|WSS Username Token Profile 1.1|http:\/\/docs.oasis\-open.org\/wss\/2004\/01\/oasis\-200401\-wss\-username\-token\-profile\-1.0.pdf|  
|WSS : X.509 Token Profile 1,1|http:\/\/www.oasis\-open.org\/committees\/download.php\/16785\/wss\-v1.1\-spec\-os\-x509TokenProfile.pdf|  
|WSS: Kerberos Token Profile 1.1|http:\/\/www.oasis\-open.org\/committees\/download.php\/16788\/wss\-v1.1\-spec\-os\-KerberosTokenProfile.pdf|  
|WSS: SAML 1.1 Token Profile 1.1|http:\/\/www.oasis\-open.org\/committees\/download.php\/16768\/wss\-v1.1\-spec\-os\-SAMLTokenProfile.pdf|  
|WS\-Secure Conversation|http:\/\/msdn.microsoft.com\/ws\/2005\/02\/ws\-secure\-conversation\/|  
|WS\-Trust|http:\/\/msdn.microsoft.com\/ws\/2005\/02\/ws\-trust\/|  
|Note d'application :<br /><br /> Utilisation de WS\-Trust pour la négociation TLS|À publier|  
|Note d'application :<br /><br /> Utilisation de WS\-Trust pour SPNEGO|À publier|  
|Note d'application :<br /><br /> Identité et références de point de terminaison Web Services Addressing|À publier|  
|WS\-SecurityPolicy 1.1<br /><br /> \(2005\/07\)|http:\/\/msdn.microsoft.com\/ws\/2005\/07\/ws\-security\-policy\/<br /><br /> tel qu'amendé par les errata soumis au comité technique OASIS WS\-SX http:\/\/www.oasis\-open.org\/archives\/ws\-sx\/200512\/msg00017.html|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] version 1 fournit 17 modes d'authentification qui peuvent être utilisés comme base pour la configuration de sécurité des services Web.  Chaque mode est optimisé pour un jeu commun de spécifications de déploiement, tel que :  
  
-   Informations d'identification utilisées pour authentifier le client et le service.  
  
-   Mécanismes de protection de la sécurité des messages et du transport.  
  
-   Modèles d'échange de messages.  
  
|Mode d'authentification|Authentification de client|Authentification de serveur|Mode|  
|-----------------------------|--------------------------------|---------------------------------|----------|  
|UserNameOverTransport|Nom d'utilisateur\/mot de passe|X509|Transport|  
|CertificateOverTransport|X509|X509|Transport|  
|KerberosOverTransport|Windows|X509|Transport|  
|IssuedTokenOverTransport|Fédérée|X509|Transport|  
|SspiNegotiatedOverTransport|Windows Sspi Negotiated|Windows Sspi Negotiated|Transport|  
|AnonymousForCertificate|None|X509|Message|  
|UserNameForCertificate|Nom d'utilisateur\/mot de passe|X509|Message|  
|MutualCertificate|X509|X509|Message|  
|MutualCertificateDuplex|X509|X509|Message|  
|IssuedTokenForCertificate|Fédérée|X509|Message|  
|Kerberos|Windows|Windows|Message|  
|IssuedToken|Fédérée|Fédérée|Message|  
|SspiNegotiated|Windows Sspi Negotiated|Windows Sspi Negotiated|Message|  
|AnonymousForSslNegotiated|None|X509, TLS\-Nego|Message|  
|UserNameForSslNegotiated|Nom d'utilisateur\/mot de passe|X509, TLS\-Nego|Message|  
|MutualSslNegotiated|X509|X509, TLS\-Nego|Message|  
|IssuedTokenForSslNegotiated|Fédérée|X509, TLS\-Nego|Message|  
  
 Les points de terminaison qui utilisent des modes d'authentification de ce type peuvent exprimer leurs conditions de sécurité à l'aide de WS\-SP \(WS\-SecurityPolicy\).  Ce document décrit la structure des messages d'infrastructure et d'en\-tête de sécurité pour chaque mode d'authentification et fournit des exemples de stratégies et de messages.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tire parti de WS\-SecureConversation pour assurer la prise en charge des sessions sécurisées afin de protéger les échanges multi\-messages entre les applications.  Consultez la section « Sessions sécurisées » ci\-après pour plus d'informations sur l'implémentation.  
  
 Outre les modes d'authentification, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des paramètres pour contrôler les mécanismes de protection courants qui s'appliquent à la plupart des modes d'authentification basés sur la sécurité du message, par exemple : ordre de signature et opérations de chiffrement, suites algorithmiques, dérivation de clé et confirmation de signature.  
  
 Les préfixes et espaces de noms suivants sont utilisés dans ce document.  
  
|Préfixe|Espace de noms|  
|-------------|--------------------|  
|s|http:\/\/www.w3.org\/2003\/05\/soap\-envelope|  
|sp|http:\/\/schemas.xmlsoap.org\/ws\/2005\/07\/securitypolicy|  
|a|http:\/\/www.w3.org\/2005\/08\/addressing \(page pouvant être en anglais\)|  
|wsse|TBD \- URI OASIS WSS 1,0|  
|wsse11|TBD \- URI OASIS WSS 1.1|  
|wsu|TBD \- URI OASIS WSS 1.0 Utility|  
|ds|TBD \- URI W3C XMLDSig|  
|wst|TBD \- URI WS\-Trust 2005\/02|  
|wssc|TBD \- URI WS\-SecureConversation 2005\/02|  
|wsaw|TBD \- espace de noms de stratégie WS\-Addressing|  
|wsp|http:\/\/schemas.xmlsoap.org\/ws\/2004\/09\/policy|  
|mssp|http:\/\/schemas.microsoft.com\/ws\/2005\/07\/securitypolicy|  
  
## 1.Profils de jeton  
 Les spécifications Web Services Security représentent les informations d'identification sous forme de jetons de sécurité.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les types de jetons suivants :  
  
### 1.1 UsernameToken  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suit les profils UsernameToken10 et UsernameToken11 avec les contraintes suivantes :  
  
 R1101 \- L'attribut PasswordType sur l'élément UsernameToken\\Password DOIT être omis ou avoir la valeur \#PasswordText \(valeur par défaut\).  
  
 Il est possible d'implémenter \#PasswordDigest à l'aide de l'extensibilité.  Il a été observé que \#PasswordDigest était souvent considéré à tort comme un mécanisme de protection par mot de passe suffisamment sécurisé.  Mais \#PasswordDigest ne peut pas servir de substitut pour le chiffrement de UsernameToken.  L'objectif principal de \#PasswordDigest est la protection contre des attaques par relecture.  En modes d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les menaces d'attaque par relecture sont atténuées en utilisant des signatures de message.  
  
 B1102 \- [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'émet jamais les sous\-éléments Nonce et Created de UsernameToken.  
  
 Ces sous\-éléments ont pour but de permettre la détection de relecture.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise à la place des signatures de message.  
  
 OASIS WSS SOAP Message Security UsernameToken Profile 1.1 \(UsernameToken11\) a introduit la fonctionnalité de dérivation de clé à partir du mot de passe.  
  
 B1103 \- Le mot de passe UsernameToken NE DOIT PAS être utilisé pour la dérivation de clé et, par conséquent, pour les opérations de chiffrement.  
  
 Raisonnement : les mots de passe sont généralement considérés comme trop faibles pour être utilisés dans les opérations de chiffrement.  
  
### 1.2 Jeton X509  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traite les certificats X509v3 comme une information d'identification et suit X509TokenProfile1.0 et X509TokenProfile1.1 avec les contraintes suivantes :  
  
 R1201 \- L'attribut ValueType sur l'élément BinarySecurityToken doit avoir la valeur \#X509v3 lorsqu'il contient un certificat X509v3.  
  
 WSS X509 Token Profile 1.0 et 1.1 définissent également \#X509PKIPathv1 et \#PKCS7 comme types de valeur.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge ces types.  
  
 R1202 \- Si une extension SubjectKeyIdentifier \(SKI\) est présente dans un certificat X509, wsse:KeyIdentifier doit être utilisé pour les références externes au jeton, avec l'attribut ValueType comme \#X509SubjectKeyIdentifier et son contenu comme valeur encodée en base 64 de l'extension SKI du certificat.  
  
 Les références SKI sont largement implémentées et s'avèrent être un type de référence externe hautement interopérable.  
  
 R1203 \- Une Référence externe au jeton de sécurité X509 NE DOIT PAS utiliser ds:X509IssuerSerial.  
  
 R1204 \- Si X509TokenProfile1.1 est utilisé, une référence externe au jeton de sécurité X509 DOIT utiliser l'empreinte numérique introduite par WS\-Security 1.1.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge X509IssuerSerial.  Toutefois, X509IssuerSerial pose des problèmes d'interopérabilité : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise une chaîne pour comparer deux valeurs de X509IssuerSerial.  Par conséquent, si l'une réorganise des composants du nom de sujet et envoie à un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] une référence à un certificat, elle est introuvable.  
  
### 1.3 Jeton Kerberos  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge KerberosTokenProfile1.1 à des fins d'authentification Windows avec les contraintes suivantes :  
  
 R1301 \- Un jeton Kerberos doit contenir la valeur d'un AP\_REQ Kerberos v4 encapsulé GSS tel que défini dans GSS\_API et la spécification Kerberos, et l'attribut ValueType doit avoir la valeur \#GSS\_Kerberosv5\_AP\_REQ.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise un AP\-REQ Kerberos encapsulé GSS, et non pas un AP\-REQ nu.  Il s'agit d'une méthode conseillée en matière de sécurité.  
  
### 1.4 Jeton SAML v1.1  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les profils de jeton WSS SAML 1.0 et 1.1 des jetons SAML v1.1.  Il est possible d'implémenter d'autres versions de formats de jeton SAML.  
  
### 1.5 Jeton de contexte de sécurité  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge le jeton de contexte de sécurité \(SCT\) introduit dans WS\-SecureCoversation.  Le SCT est utilisé pour représenter un contexte de sécurité établi dans SecureConversation ainsi que les protocoles de négociation binaire TLS et SSPI, tel que décrit ci\-après.  
  
## 2.Paramètres de sécurité de message courants  
  
### 2.1 TimeStamp  
 La présence de l'horodatage est contrôlée à l'aide de la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> .  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sérialise systématiquement wsse:TimeStamp avec les champs wsse:Created et wsse:Expires.  wsse:TimeStamp est systématiquement signé en cas de signature.  
  
### 2.2 Ordre de protection  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'ordre de protection de message « Sign Before Encrypt » et « Encrypt Before Sign » \(Security Policy 1.1\). "  « Sign Before Encrypt » est recommandé dans les cas suivants : les messages protégés à l'aide de Encrypt Before Sign sont ouverts aux attaques par substitution de signature, sauf si le mécanisme WS\-Security 1.1 SignatureConfirmation est utilisé et qu'une signature sur contenu chiffré rend l'audit plus difficile.  
  
### 2.3 Protection de la signature  
 Lorsque Encrypt Before Sign est utilisé, il est recommandé de protéger la signature afin d'empêcher les attaques par force brute de découvrir le contenu chiffré ou la clé de signature \(en particulier lorsqu'un jeton personnalisé est utilisé avec du matériel de clé faible\).  
  
### 2.4 Suite algorithmique  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge toutes les suites algorithmiques répertoriées dans Security Policy 1.1.  
  
### 2.5 Dérivation de clé  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la « dérivation de clé pour clés symétriques », tel que décrit dans WS\-SecureConversation.  
  
### 2.6 Confirmation de signature  
 La confirmation de signature peut se résumer à la protection contre les attaques de type « homme du milieu » afin de protéger le jeu de signatures.  
  
### 2.7 Disposition de l'en\-tête de sécurité  
 Chaque mode d'authentification décrit une certaine disposition de l'en\-tête de sécurité.  Ses éléments sont semi\-organisés.  Pour définir l'ordre des éléments enfants, WS\-Security Policy définit les modes de disposition suivants :  
  
|||  
|-|-|  
|Strict|Les éléments sont ajoutés à l'en\-tête de sécurité selon les règles de disposition numérotée décrites dans Stratégie de sécurité à la section 7.7.1 conformément à un principe général de « déclaration avant utilisation ».|  
|Lax|Les éléments sont ajoutés à l'en\-tête de sécurité dans n'importe quel ordre conforme à WSS: SOAP Message Security.|  
|LaxTimestampFirst|Identique à Lax, excepté que le premier élément dans l'en\-tête de sécurité doit être un wsse:Timestamp|  
|LaxTimestampLast|Identique à Lax, excepté que le dernier élément dans l'en\-tête de sécurité doit être un wsse:Timestamp|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'ensemble des quatre modes de disposition d'en\-tête de sécurité.  Les exemples de message et de structure d'en\-tête de sécurité fournis pour les modes d'authentification ci\-après suivent le mode « Strict ».  
  
## 2.Paramètres de sécurité de message courants  
 Cette section fournit des exemples de stratégie pour chaque mode d'authentification ainsi que des exemples qui présentent la structure d'entête de sécurité dans les messages échangés par le client et le service.  
  
### 6.1 Protection du transport  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit cinq modes d'authentification qui utilisent le transport sécurisé pour protéger les messages : UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport et SspiNegotiatedOverTransport.  
  
 Ces modes d'authentification sont construits à l'aide de la liaison de transport décrite dans SecurityPolicy.  Pour le mode d'authentification UserNameOverTransport, UsernameToken est un jeton de prise en charge signé.  Pour les autres modes d'authentification, le jeton apparaît sous forme d'un jeton d'endossement signé.  Les annexes C.1.2 et C.1.3 de SecurityPolicy décrivent en détail la disposition de l'en\-tête de sécurité.  Les exemples suivants affichent la disposition Strict pour un mode d'authentification donné.  
  
 La valeur de la propriété « Derived Keys » pour les jetons est dans tous les cas « false ».  
  
 Les valeurs des diverses propriétés de la liaison de transport sont les suivantes :  
  
 Horodateur : true  
  
 Disposition de l'en\-tête de sécurité : Strict  
  
 Suite algorithmique : Basic256  
  
#### 6.1.1 UsernameOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé qui est systématiquement envoyé de l'initiateur au destinataire.  Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.  La liaison utilisée est une liaison de transport.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Disposition de l'en\-tête de sécurité  
  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### 6.1.2 CertificateOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.  Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.  La liaison utilisée est une liaison de transport.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Disposition de l'en\-tête de sécurité  
  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### 6.1.3 IssuedTokenOverTransport  
 Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un service d'émission de jeton de sécurité \(STS\) et prouve qu'il connaît une clé partagée.  Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.  Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.  La liaison utilisée est une liaison de transport.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Disposition de l'en\-tête de sécurité  
  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### 6.1.4 KerberosOverTransport  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.  Le jeton Kerberos apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.  Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.  La liaison utilisée est une liaison de transport.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Disposition de l'en\-tête de sécurité  
  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### 6.1.5 SspiNegotiatedOverTransport  
 Avec ce mode, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.  Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM.  Le SCT résultant apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.  Le service est en outre authentifié au niveau de la couche de transport par un certificat X.509.  La liaison utilisée est une liaison de transport. "  « SPNEGO » \(négociation\) décrit comment [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise le protocole de négociation binaire SSPI avec WS\-Trust.  Les exemples d'en\-tête de sécurité présentés dans cette section supposent que le SCT a déjà été établi via la négociation SPNEGO.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité  
 Une fois que le jeton de contexte de sécurité est établi via la négociation SPNEGO à l'aide de WS\-Trust Binary Negotiation, les messages d'application ont des en\-têtes de sécurité présentant la structure suivante.  
  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### 6.2 Utilisation des certificats X.509 pour l'authentification de service  
 Cette section décrit les modes d'authentification suivants : MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate et IssuedTokenForCertificate.  
  
#### 6.2.1 MutualCertificate WSS1.0  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme de jeton d'initiateur.  Le service est également authentifié à l'aide d'un certificat X.509.  
  
 La liaison utilisée est une liaison asymétrique avec les valeurs de propriété suivantes :  
  
 Jeton d'initiateur : certificat X.509 du client, avec mode d'inclusion défini à …\/IncludeToken\/AlwaysToRecipient  
  
 Jeton de destinataire : certificat X.509 du serveur, avec mode d'inclusion défini à …\/IncludeToken\/Never  
  
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Exemples d'en\-tête de sécurité : EncryptBeforeSign  
  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.2.2 MutualCertificateDuplex  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme de jeton d'initiateur.  Le service est également authentifié à l'aide d'un certificat X.509.  
  
 La liaison utilisée est une liaison asymétrique avec les valeurs de propriété suivantes :  
  
 Jeton d'initiateur : certificat X509 du client, avec mode d'inclusion défini à …\/IncludeToken\/AlwaysToRecipient  
  
 Jeton de destinataire : certificat X509 du serveur, avec mode d'inclusion défini à …\/IncludeToken\/AlwaysToInitiator  
  
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Demande et réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Demande et réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.2.3 Utilisation de SymmetricBinding avec l'authentification de service X.509  
 « WSS10 » a fourni un support limité aux scénarios avec jetons X509.  Par exemple, il n'était pas possible d'assurer la protection des signatures et du chiffrement des messages qui utilisent uniquement le jeton X509 du service. "  WSS11 » a introduit l'utilisation de EncryptedKey sous forme d'un jeton symétrique.  Une clé temporaire chiffrée pour le certificat X.509 du service peut maintenant être utilisée à la fois pour la protection des messages de demande et de réponse.  Les modes d'authentification décrits dans la section 6.4 ci\-après utilisent ce modèle.  
  
 WS\-SecurityPolicy décrit ce modèle à l'aide de SymmetricBinding avec le jeton X509 du service sous forme de jeton de protection.  
  
 Les modes d'authentification AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 et IssuedTokenForCertificate utilisent tous une instance similaire de sp:SymmetricBinding avec les valeurs de propriété suivantes :  
  
 Jeton de protection : certificat X509 du serveur, avec mode d'inclusion défini à ...\/IncludeToken\/Never                   
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Les modes d'authentification précédemment cités diffèrent uniquement par les jetons de prise en charge qu'ils utilisent.  AnonymousForCertificate n'a pas de jeton de prise en charge, MutualCertificate WSS 1.1 a le certificat X509 du client comme jeton de prise en charge d'endossement, UserNameForCertificate a un jeton de nom d'utilisateur comme jeton de prise en charge signé, et IssuedTokenForCertificate a le jeton émis sous forme d'un jeton de prise en charge d'endossement.  
  
 Stratégie  
  
 Liaison symétrique  
  
```  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### 6.2.4 AnonymousForCertificate  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509.  La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.4.2.  
  
 Stratégie  
  
 Consultez « Stratégie » à la section 6.2.3 ci\-dessus pour plus d'informations sur la liaison.  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.2.5 UserNameForCertificate  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé.  Le service s'authentifie auprès du client à l'aide d'un certificat X.509.  La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.  
  
 Stratégie  
  
 Consultez « Stratégie » à la section 6.2.3 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge signé  
  
```  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.2.6 MutualCertificate \(WSS 1.1\)  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.  Le service est également authentifié à l'aide d'un certificat X.509.  La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.  
  
 Stratégie  
  
 Consultez « Stratégie » à la section 6.2.3 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge d'endossement  
  
```  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.2.7 IssuedTokenForCertificate  
 Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.  Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.  Le service s'authentifie auprès du client à l'aide d'un certificat X.509.  La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.  
  
 Stratégie  
  
 Consultez « Stratégie » à la section 6.2.3 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge d'endossement  
  
```  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## 6.3 Kerberos  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.  Ce même ticket fournit également l'authentification de serveur.  La liaison utilisée est une liaison symétrique avec les propriétés suivantes :  
  
 Jeton de protection : Ticket Kerberos, avec mode d'inclusion défini à …\/IncludeToken\/Once           
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### 6.4 IssuedToken  
 Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.  Le service n'est pas authentifié auprès du client, en tant que tel, mais le STS chiffre la clé partagée dans le cadre du jeton émis afin que seul le service puisse déchiffrer la clé.  La liaison utilisée est une liaison symétrique avec les propriétés suivantes :  
  
 Jeton de protection : Jeton émis, avec mode d'inclusion défini à ...\/IncludeToken\/AlwaysToRecipient                   
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### 6.5 Utilisation de SslNegotiated pour l'authentification de service  
 Cette section décrit un groupe de modes d'authentification qui utilisent une liaison symétrique, le jeton de protection étant un jeton de contexte de sécurité tel que défini dans WS\-SC \(WS\-SecureConversation\) dont la valeur de clé est négociée en exécutant le protocole TLS sur les messages WS\-T \(WS\-Trust\) RST\/RSTR.  Les détails de l'implémentation de la négociation TLS à l'aide de WS\-Trust sont décrits dans TLSNEGO.  Dans les exemples de message présentés, nous supposerons que le SCT avec un contexte de sécurité associé est déjà établi via une négociation.  
  
 La liaison utilisée est une liaison symétrique avec les propriétés suivantes :  
  
 Jeton de protection : SslContextToken, avec mode d'inclusion défini à ...\/IncludeToken\/Never               
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
#### 6.5.1 Stratégie d'authentification de service SslNegotiated  
 La stratégie utilisée pour tous les modes d'authentification présentés dans cette section est similaire et diffère uniquement par les jetons d'endossement ou de prise en charge signés spécifiques utilisés.  
  
```  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### 6.5.2 AnonymousForSslNegotiated  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509.  La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci\-dessus.  
  
 Stratégie  
  
 Consultez « Stratégie » à la section 6.5.1 ci\-dessus pour plus d'informations sur la liaison.  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.5.3 UserNameForSslNegotiated  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé.  Le service est authentifié à l'aide d'un certificat X.509.  La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1.  
  
 Stratégie  
  
 Consultez la section 6.5.1 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge signé  
  
```  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.5.4 IssuedTokenForSslNegotiated  
 Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.  Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.  Le service est authentifié à l'aide d'un certificat X.509.  La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci\-dessus.  
  
 Stratégie  
  
 Consultez la section 6.5.1 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge d'endossement  
  
```  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### 6.5.5 MutualSslNegotiated  
 Avec ce mode d'authentification, le client et le service s'authentifient à l'aide de certificats X.509.  La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci\-dessus.  
  
 Stratégie  
  
 Consultez la section 6.5.1 ci\-dessus pour plus d'informations sur la liaison.  
  
 Jeton de prise en charge d'endossement  
  
```  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### 6.6 SspiNegotiated  
 Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.  Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM.  La liaison utilisée est une liaison symétrique avec les propriétés suivantes :  
  
 Jeton de protection : SpnegoContextToken, avec mode d'inclusion défini à ...\/IncludeToken\/AlwaysToRecipient               
 Jeton de protection : False  
  
 Signatures du corps et de l'intégralité de l'en\-tête : True  
  
 Ordre de protection : SignBeforeEncrypt  
  
 Chiffrement de la signature : True  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### 6.7 SecureConversation  
 La liaison utilisée est une liaison symétrique, le jeton de protection étant un SCT tel que défini dans WS\-SC \(WS\-SecureConversation\).  Le SCT est négocié à l'aide de WS\-T \(WS\-Trust\) ou WS\-SC \(WS\-SecureConversation\) d'après une liaison imbriquée, qui est elle\-même une liaison symétrique utilisant un protocole de négociation.  Le protocole de négociation utilisera Kerberos pour effectuer l'authentification du client et du serveur, si possible.  Si Kerberos ne peut pas être utilisé, ce sera NTLM.  
  
 Stratégie  
  
```  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### Exemples d'en\-tête de sécurité : SignBeforeEncrypt, EncryptSignature  
 Requête  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### Exemples d'en\-tête de sécurité : EncryptBeforeSign  
 Requête  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Réponse  
  
```  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```