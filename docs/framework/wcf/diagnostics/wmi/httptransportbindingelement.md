---
title: "HttpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HttpTransportBindingElement
HttpTransportBindingElement  
  
## Syntaxe  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## Méthodes  
 La classe HttpTransportBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe HttpTransportBindingElement a les propriétés suivantes :  
  
### AllowCookies  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le client accepte les cookies et les propage aux demandes suivantes.  
  
### AuthenticationScheme  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un écouteur HTTP.  
  
### BypassProxyOnLocal  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si les proxys sont ignorés pour les adresses locales.  
  
### HostNameComparisonMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le nom d'hôte est utilisé pour accéder au service lors de la correspondance sur l'URI.  
  
### KeepAliveEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 En cas d'activation, les connexions HTTP sont maintenues indépendamment du niveau d'activité.  
  
### MaxBufferSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille maximale du pool de mémoires tampons.  
  
### ProxyAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 URI qui contient l'adresse du proxy à utiliser pour les requêtes HTTP.  
  
### ProxyAuthenticationScheme  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un proxy HTTP.  
  
### Realm  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Domaine d'authentification.  
  
### TransferMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.  
  
### UnsafeConnectionNtlmAuthentication  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le partage de connexion non sécurisé est activé sur le serveur.  
  
### UseDefaultWebProxy  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si les paramètres de proxy à l'échelle de l'ordinateur sont utilisés à la place des paramètres propres à l'utilisateur.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>