---
title: "TcpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TcpTransportBindingElement
TcpTransportBindingElement  
  
## Syntaxe  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## Méthodes  
 La classe TcpTransportBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe TcpTransportBindingElement a les propriétés suivantes :  
  
### ConnectionPoolSettings  
 Type de données : TcpConnectionPoolSettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de pool de connexions.  
  
### ListenBacklog  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de demandes de connexion en file d'attente pouvant être en attente.  
  
### PortSharingEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.  
  
### TeredoEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si Teredo \(technologie d'adressage de clients placés derrière des pare\-feu\) est activé.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>