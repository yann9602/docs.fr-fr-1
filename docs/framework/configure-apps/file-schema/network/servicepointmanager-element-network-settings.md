---
title: "&lt;servicePointManager&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 85ccad3e2c3b237e286f3737589a5e58994521bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;servicePointManager&gt; élément (paramètres réseau)
Configure les connexions aux ressources réseau.  
  
 \<configuration>  
\<System.NET >  
\<Paramètres >  
\<servicePointManager >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`checkCertificateName`|Spécifie si le système doit vérifier que le nom du certificat correspond le nom d’hôte du serveur avant d’utiliser le certificat. La valeur par défaut est `true`.|  
|`checkCertificateRevocationList`|Spécifie si le système doit vérifier si le certificat a été révoqué avant d’utiliser le certificat. La valeur par défaut est `false`.|  
|`dnsRefreshTimeout`|Spécifie la durée pendant laquelle Service DNS (Domain Name) résolutions sont mis en cache avec l’option de tourniquet DNS, en millisecondes. La valeur par défaut est 120 000 millisecondes (deux minutes).|  
|`enableDnsRoundRobin`|Spécifie si les résolutions DNS d’hôte noms avec plusieurs adresses IP (Internet Protocol) retournés toutes les adresses, ou simplement la première. La valeur par défaut est `false`.|  
|`encryptionPolicy`|Spécifie la stratégie de chiffrement appliquée à une session SSL/TLS sur un <xref:System.Net.ServicePointManager> instance. Les valeurs possibles sont équivalents aux valeurs de la <xref:System.Net.Security.EncryptionPolicy> énumération. L’utilisation de <xref:System.Security.Authentication.CipherAlgorithmType.Null> est requise lors de la stratégie de chiffrement a la valeur `NoEncryption`. La valeur par défaut est `RequireEncryption`.|  
|`expect100Continue`|Spécifie si les méthodes POST doivent s’attendre à recevoir un `100-continue` réponse du serveur. La valeur par défaut est `true`.|  
|`useNagleAlgorithm`|Spécifie si les connexions contrôlées par le Gestionnaire de point de service utilisent l’algorithme Nagle. La valeur par défaut est `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
