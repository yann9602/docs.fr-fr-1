---
title: "Security ETW Events | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security events [.NET Framework]"
  - "ETW, security events (CLR)"
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Security ETW Events
<a name="top"></a> Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.  
  
 Cette catégorie comprend les événements suivants :  
  
-   [Événements StrongNameVerificationStart\_V1 et StrongNameVerificationStop\_V1](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [Événements AuthenticodeVerificationStart\_V1 et AuthenticodeVerificationStop\_V1](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## Événements StrongNameVerificationStart\_V1 et StrongNameVerificationStop\_V1  
 Le tableau suivant montre les mots clés et les niveaux. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`SecurityKeyword` \(0x400\)|Informatif\(4\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`StrongNameVerificationStart_V1`|181|Début de la vérification de nom fort.|  
|`StrongNameVerificationStop_V1`|182|Fin de la vérification de nom fort.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|VerificationFlags|win:UInt32|Indicateurs de vérification.|  
|ErrorCode|win:UInt32|Code d'erreur HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|Nom d'assembly qualifié complet.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## Événements AuthenticodeVerificationStart\_V1 et AuthenticodeVerificationStop\_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`SecurityKeyword` \(0x400\)|Informatif\(4\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`AuthenticodeVerificationStart_V1`|183|Début de la vérification Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Fin de la vérification Authenticode.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|VerificationFlags|win:UInt32|Indicateurs de vérification.|  
|ErrorCode|win:UInt32|Code d'erreur HResult.|  
|ModulePath|win:UnicodeString|Chemin d’accès du module.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)