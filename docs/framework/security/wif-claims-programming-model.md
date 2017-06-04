---
title: "Mod&#232;le de programmation de revendications WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# Mod&#232;le de programmation de revendications WIF
ASP.NET et Windows Communication Foundation \(WCF\) ont généralement pas utiliser les interfaces IIdentity et IPrincipal pour travailler avec les informations d'identité de l'utilisateur.  Dans.NET 4.5, Windows Identity Foundation \(WIF\) a été intégré tel que les revendications sont désormais toujours présentes pour n'importe quelle entité comme illustré dans le diagramme suivant :  
  
 ![Modèle de programmation de revendications WIF](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 Dans.NET 4.5, System.Security.Claims contient les nouvelles classes ClaimsPrincipal et ClaimsIdentity \(voir diagramme ci\-dessus\).  Toutes les entités de sécurité dans.NET est maintenant dériver de ClaimsPrincipal.  Toutes les classes d'identité intégrés, comme FormsIdentity d'ASP.NET et WindowsIdentity maintenant dérivent de ClaimsIdentity.  De même, toutes les principales classes intégrées comme GenericPrincipal et WindowsPrincipal dérivent de ClaimsPrincipal.  
  
 Une revendication est représentée par <xref:System.Security.Claims.Claim> classe.  Cette classe possède les propriétés importantes suivantes :  
  
-   <xref:System.Security.Claims.Claim.Type%2A>représente le type de revendication et est généralement un URI.  Par exemple, la revendication d'adresse de courrier électronique est représentée sous la forme `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.  
  
-   <xref:System.Security.Claims.Claim.Value%2A>contient la valeur de la créance et est représenté sous forme de chaîne.  Par exemple, l'adresse de messagerie peut être représentée en tant que « personne@contoso.com ».  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A>représente le type de la valeur de revendication et est généralement un URI.  Par exemple, le type de chaîne est représenté en tant que `http://www.w3.org/2001/XMLSchema#string`.  Le type valeur doit être un QName conformément au schéma XML.  La valeur doit être au format `namespace#format` pour activer la WIF produire une valeur QName valide.  Si l'espace de noms n'est pas un espace de noms bien défini, le code XML généré probablement impossible schéma validé, car il sera pas un fichier XSD publié pour cet espace de noms.  Le type de valeur par défaut est `http://www.w3.org/2001/XMLSchema#string`.  Veuillez vous reporter à [http:\/\/www.w3.org\/2001\/XMLSchema](http://go.microsoft.com/fwlink/?LinkId=209155) pour les types de valeur bien connu que vous pouvez utiliser en toute sécurité.  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A>est l'identificateur de la service de jeton de sécurité \(STS\) qui a émis la demande.  Cela peut être représentée comme URL de l'enquête STS ou un nom qui représente le STS, telle que `https://sts1.contoso.com/sts`.  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A>est l'identificateur de l'enquête STS qui a émis la demande, indépendamment de la STSs combien sont dans la chaîne.  Cette opération est représentée comme <xref:System.Security.Claims.Claim.Issuer%2A>.  
  
-   <xref:System.Security.Claims.Claim.Subject%2A>est le sujet dont l'identité est en cours d'examen.  Il contient un <xref:System.Security.Claims.ClaimsIdentity>.  
  
-   <xref:System.Security.Claims.Claim.Properties%2A>est un dictionnaire qui permet au développeur de fournir des données spécifiques à l'application doivent être transférés sur le câble avec les autres propriétés et peut être utilisé pour la validation personnalisée.  
  
## Délégation de l'identité  
 Une propriété importante de <xref:System.Security.Claims.ClaimsIdentity> est <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>.  Cette propriété permet la délégation d'informations d'identification dans un système multi\-niveaux dans laquelle une couche intermédiaire agit comme le client pour effectuer des demandes à un service back\-end.  
  
### L'accès à des revendications via Thread.CurrentPrincipal  
 Pour accéder à ensemble l'utilisateur actuel de revendications dans une application RP, utilisez `Thread.CurrentPrincipal`.  
  
 L'exemple de code suivant illustre l'utilisation de cette méthode pour obtenir un System.Security.Claims.ClaimsIdentity :  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
```  
  
 Pour plus d'informations, consultez <xref:System.Security.Claims>.  
  
### Type de revendication de rôle  
 Partie de la configuration de votre application RP consiste à déterminer quel rôle votre réclamation type doit être.  Ce type de revendication est utilisé par System.Security.Claims.ClaimsPrincipal.IsInRole\(System.String\).  Le type de revendication par défaut est `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.  
  
### Revendications extraites par la Fondation d'identité Windows à partir de différents Types de jeton  
 WIF prend en charge les combinaisons de plusieurs mécanismes d'authentification de la zone.  Le tableau suivant répertorie les revendications WIF extrait à partir de différents types de jetons.  
  
||||  
|-|-|-|  
|Type de jeton|Revendication générée|Carte à jeton d'accès Windows|  
|SAML 1.1|1.  Toutes les réclamations à partir de System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity\(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope\).<br />2.  Le `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` revendication qui contient la sérialisation XML de la clé de confirmation, si le jeton contient un jeton de preuve.<br />3.  Le `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` réclamer à l'élément de l'émetteur.<br />4.  Revendications AuthenticationMethod et AuthenticationInstant, si le jeton contient une instruction d'authentification.|Outre les revendications répertoriés dans « SAML 1.1 », à l'exception des déclarations de type `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, liés à l'authentification Windows revendications seront ajoutées et l'identité sera représentée par WindowsClaimsIdentity.|  
|SAML 2.0|Identique à « SAML 1.1 ».|Identique à « SAML 1.1 mappé au compte Windows ».|  
|X509|1.  Revendications avec le X 500 distinguant nom nommessagerie, NomDNS, SimpleName, UpnName, UrlName, empreinte, RsaKey \(cela peut être extrait à l'aide de la méthode RSACryptoServiceProvider.ExportParameters à partir de la propriété X509Certificate2.PublicKey.Key\), DsaKey \(cela peut être extrait à l'aide de la méthode DSACryptoServiceProvider.ExportParameters à partir de la propriété X509Certificate2.PublicKey.Key\), propriétés SerialNumber depuis le X 509 certificat.<br />2.  Revendication AuthenticationMethod avec la valeur `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`.  Revendication de AuthenticationInstant avec la valeur du temps lorsque le certificat a été validé dans le format XmlSchema DateTime.|1.  Il utilise le nom de domaine pleinement qualifié du compte Windows comme la `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` valeur de la demande.  .<br />2.  Créances à partir de la X 509 certificat mappé non Windows et revendications à partir du compte windows obtenue en mappant les certificats pour Windows.|  
|UPN|1.  Revendications sont similaires pour les revendications contenues dans la section de l'authentification Windows.<br />2.  Revendication AuthenticationMethod avec la valeur `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`.  La revendication de AuthenticationInstant avec la valeur du temps lorsque le mot de passe a été validé dans le format XmlSchema DateTime.||  
|Windows \(Kerberos ou NTLM\)|1.  Revendications générées à partir du jeton d'accès tels que : PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, SIDgroupe, DenyOnlySID et le nom<br />2.  AuthenticationMethod avec la valeur `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`.  AuthenticationInstant avec la valeur du jeton d'accès lorsque les fenêtres de temps a été créé dans le format XMLSchema DateTime.||  
|Paire de clés RSA|1.  Le `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` revendiquer avec la valeur de RSAKeyValue.<br />2.  Revendication AuthenticationMethod avec la valeur `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`.  Revendication de AuthenticationInstant avec la valeur du temps lorsque la clé RSA a été authentifiée \(autrement dit, la signature a été vérifiée\) dans le format XMLSchema DateTime.||  
  
|||  
|-|-|  
|Type d'authentification|URI émis en revendication « AuthenticationMethod »|  
|Mot de passe|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Non spécifié|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|