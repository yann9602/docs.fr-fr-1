---
title: "Sch&#233;ma des param&#232;tres r&#233;seau | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "paramètres de configuration (.NET Framework), réseaux"
  - "connexions (.NET Framework), éléments de configuration réseau"
  - "éléments (.NET Framework), éléments de configuration réseau"
  - "Internet, éléments de configuration réseau"
  - "éléments de configuration réseau"
  - "ressources réseau, éléments de configuration réseau"
  - "paramètres réseau"
  - "recevoir des données, éléments de configuration réseau"
  - "envoyer des données, éléments de configuration réseau"
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# Sch&#233;ma des param&#232;tres r&#233;seau
Les Paramètres de Réseaux spécifient la manière dont le .NET Framework se connecte au réseau.  Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous le [\<system.Net\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authenticationModules\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Spécifie les modules qui servent à authentifier les demandes Internet.|  
|[\<connectionManagement\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à des hôtes Internet.|  
|[\<defaultProxy\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Spécifie le serveur proxy utilisé pour les requêtes HTTP envoyées vers Internet.|  
|[\<mailSettings\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Contient des paramètres pour les options d'envoi de courrier électronique.|  
|[\<requestCaching\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Spécifie les modules qui servent à demander des informations à des hôtes Internet.|  
|[\<requestCaching\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net?displayProperty=fullName>.|  
|[\<webRequestModules\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Spécifie les modules qui servent à demander des informations à des hôtes Internet.|  
  
 Les Paramètres Uri spécifient la manière dont le .NET Framework gère des adresses Web exprimées à l'aide d'identificateurs URI \(Uniform Resource Identifiers\).  Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous le [\<Uri\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<idn\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Spécifie si l'analyse de l'IDN \(Internationalized Domain Name\) est appliquée aux noms de domaines.|  
|[\<iriParsing\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Spécifie si l'analyse IRI \(International Resource Identifier\) est appliquée à un <xref:System.Uri> et si les règles d'analyse de l'identificateur IRI doivent être appliquées.|  
|[\<schemeSettings\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Spécifie comment un <xref:System.Uri> sera analysé pour des schémas spécifiques.|  
  
## Voir aussi  
 [Configuration des applications Internet](../../../../../docs/framework/network-programming/configuring-internet-applications.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)