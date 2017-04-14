---
title: "&lt;servicePointManager&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<servicePointManager> (élément)"
  - "servicePointManager (élément)"
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# &lt;servicePointManager&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Configure des connexions aux ressources réseau.  
  
## Syntaxe  
  
```  
  
      <servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`checkCertificateName`|Spécifie si le système doit vérifier que le nom sur le certificat correspond au nom d'hôte du serveur avant d'utiliser le certificat.  La valeur par défaut est `true`.|  
|`checkCertificateRevocationList`|Spécifie si le système doit vérifier que le certificat a été révoqué avant d'utiliser le certificat.  La valeur par défaut est `false`.|  
|`dnsRefreshTimeout`|Spécifie le délai de mise en cache, en millisecondes, des résolutions DNS avec l'option DNS Rond Robin.  La valeur par défaut est 120 000 millisecondes \(deux minutes\).|  
|`enableDnsRoundRobin`|Spécifie si les résolutions DNS des noms d'hôtes avec plusieurs adresses IP retournent toutes les adresses ou uniquement la première.  La valeur par défaut est `false`.|  
|`encryptionPolicy`|Spécifie la stratégie de chiffrement appliquée à une session SSL\/TLS sur une instance <xref:System.Net.ServicePointManager>.  Les valeurs possibles correspondent aux valeurs pour l'énumération <xref:System.Net.Security.EncryptionPolicy>.  L'utilisation de <xref:System.Security.Authentication.CipherAlgorithmType> est requise lorsque la stratégie de chiffrement a la valeur `NoEncryption`.  La valeur par défaut est `RequireEncryption`.|  
|`expect100Continue`|Spécifie si les méthodes POST doivent attendre pour recevoir une réponse `100-continue` du serveur.  La valeur par défaut est `true`.|  
|`useNagleAlgorithm`|Spécifie si les connexions contrôlées par le gestionnaire de points de service utilisent l'algorithme Nagle.  La valeur par défaut est `true`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Voir aussi  
 <xref:System.Net.ServicePointManager>   
 <xref:System.Net.Security.EncryptionPolicy>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)