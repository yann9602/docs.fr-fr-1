---
title: "MsmqBindingElementBase | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# MsmqBindingElementBase
MsmqBindingElementBase  
  
## Syntaxe  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## Méthodes  
 La classe MsmqBindingElementBase ne définit pas de méthode.  
  
## Propriétés  
 La classe MsmqBindingElementBase a les propriétés suivantes :  
  
### CustomDeadLetterQueue  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 URI qui contient l'emplacement de la file d'attente de lettres mortes pour chaque application, dans laquelle les messages expirés ou dont le transfert ou la remise a échoué sont placés.  
  
### DeadLetterQueue  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur d'énumération qui indique le type de la file d'attente de lettres mortes à utiliser.  
  
### Durable  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si les messages traités par cette liaison sont durables ou volatils.  
  
### ExactlyOnce  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison sont reçus exactement une fois.  
  
### MaxRetryCycles  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de cycles de nouvelle tentative de livraison de messages à l'application de réception.  
  
### ReceiveErrorHandling  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres de gestion de messages incohérents.  
  
### ReceiveRetryCount  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de nouvelles tentatives immédiates sur un message qui est lu à partir de la file d'attente d'application.  
  
### RetryCycleDelay  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique l'intervalle entre des cycles de nouvelle tentative de remise d'un message n'ayant pas pu être remis immédiatement.  
  
### TimeToLive  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle qui indique combien de temps les messages traités par cette liaison peuvent séjourner dans la file d'attente avant expiration.  
  
### UseMsmqTracing  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison doivent être suivis.  
  
### UseSourceJournal  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les copies des messages traités par cette liaison doivent être stockées dans la file d'attente du journal source.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.NetMsmqBinding>   
 <xref:System.ServiceModel.MsmqBindingBase>