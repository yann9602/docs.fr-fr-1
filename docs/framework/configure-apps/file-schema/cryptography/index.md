---
title: "Sch&#233;ma des param&#232;tres de chiffrement | Microsoft Docs"
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
  - "schéma de configuration (.NET Framework), chiffrement"
  - "sections de configuration (.NET Framework)"
  - "paramètres de configuration (.NET Framework), chiffrement"
  - "chiffrement, mapper des noms d'algorithmes"
  - "chiffrement, schéma des paramètres"
  - "éléments (.NET Framework), chiffrement"
  - "paramètres de configuration (schéma)"
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Sch&#233;ma des param&#232;tres de chiffrement
Le schema de paramètres de cryptographie contient des éléments qui précisent comme mapper les noms d'algorithmes amicaux aux classes qui implémentent les algorithmes de cryptographie.  
  
 [\<Configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<mscorlib\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [\<cryptoNameMapping\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [\<cryptoClasses\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [\<oidMap\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cryptoClasses\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|Contient une liste des classes de chiffrement associées à un nom convivial figurant dans l'élément **\<nameEntry\>**.|  
|[\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Contient une classe de chiffrement associée à un nom convivial figurant dans l'élément **\<nameEntry\>**.|  
|[\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|Contient des paramètres de chiffrement.|  
|[\<cryptoNameMapping\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Contient les mises en correspondance des classes avec les noms conviviaux.|  
|[\<mscorlib\>, élément pour les paramètres de chiffrement](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|Contient l'élément **\<cryptographySettings\>**.|  
|[\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|Associe un nom de classe à un nom d'algorithme convivial, ce qui permet à une seule classe d'avoir plusieurs noms conviviaux.|  
|[\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|Associe un OID \(Object IDentifier\) ASN.1 à un nom convivial.|  
|[\<oidMap\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|Contient les mises en correspondance des OID ASN.1 avec les classes.|  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Services de chiffrement](../../../../../docs/standard/security/cryptographic-services.md)