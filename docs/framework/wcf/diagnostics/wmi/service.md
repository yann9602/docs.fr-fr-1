---
title: "Service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Service
Service  
  
## Syntaxe  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## Méthodes  
 La classe Service ne définit aucune méthode.  
  
## Propriétés  
 La classe Service a les propriétés suivantes :  
  
### BaseAddresses  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les adresses de base utilisées par le service.  
  
### Comportements  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Les comportements associés à ce service.  
  
### ConfigurationName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 ServiceElement\_BehaviorConfiguration  
  
### CounterInstanceName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Le nom d'instance de l'instance des compteurs de performances du service.  
  
### DistinguishedName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom du service à cette adresse.  
  
### Extensions  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les contextes d'instance pour les extensions de l'instance de service.  
  
### Métadonnées  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les paramètres de métadonnées du service.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Le nom unique de ce service.  
  
### Espace de noms  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 L'espace de noms du service.  
  
### Opened  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 L'heure à laquelle le service a été ouvert.  
  
### OutgoingChannels  
 Type de données : tableau de canaux  
  
 Type d'accès : lecture seule  
  
 Les canaux qui sortent de l'instance de service.  
  
### ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 L'ID de processus du processus qui héberge le service.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|