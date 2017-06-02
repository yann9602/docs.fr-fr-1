---
title: "PeerSecuritySettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# PeerSecuritySettings
PeerSecuritySettings  
  
## Syntaxe  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## Méthodes  
 La classe PeerSecuritySettings ne définit pas de méthode.  
  
## Propriétés  
 La classe PeerSecuritySettings a les propriétés suivantes :  
  
### Mode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Utilisation ou non d'une sécurité au niveau du message et au niveau du transport par un point de terminaison configuré avec la liaison.  
  
### Transport  
 Type de données : PeerTransportSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de sécurité du transport.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.PeerSecuritySettings>