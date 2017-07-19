---
title: "PeerTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# PeerTransportBindingElement
PeerTransportBindingElement  
  
## Syntaxe  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## Méthodes  
 La classe PeerTransportBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe PeerTransportBindingElement a les propriétés suivantes :  
  
### ListenIPAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse IP sur laquelle le nœud homologue écoute les messages.  
  
### Port  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Port d’interface de réseau sur lequel la liaison traite les messages de canaux homologues.  
  
### Sécurité  
 Type de données : PeerSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de sécurité de transport de l'homologue.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>