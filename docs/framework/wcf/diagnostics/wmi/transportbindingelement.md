---
title: "TransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransportBindingElement
TransportBindingElement  
  
## Syntaxe  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## Méthodes  
 La classe TransportBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe TransportBindingElement a les propriétés suivantes :  
  
### ManualAddressing  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si l'utilisateur souhaite prendre le contrôle de l'adressage des messages.  
  
### MaxBufferPoolSize  
 Type de données : sint64  
  
 Type d'accès : lecture seule  
  
 Taille maximale du pool de mémoires tampons pour la liaison.  
  
### MaxReceivedMessageSize  
 Type de données : sint64  
  
 Type d'accès : lecture seule  
  
 Taille maximale d'un message traité par cette liaison.  
  
### Scheme  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Schéma d'URI pour le transport.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.TransportBindingElement>