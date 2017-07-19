---
title: "CallbackBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# CallbackBehavior
CallbackBehavior  
  
## Syntaxe  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## Méthodes  
 La classe CallbackBehavior ne définit pas de méthode.  
  
## Propriétés  
 La classe CallbackBehavior a les propriétés suivantes :  
  
### AutomaticSessionShutdown  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Lorsque sa valeur est « true », la session est fermée automatiquement lorsqu'un service ferme une session duplex.  
  
### ConcurrencyMode  
 Type de données : chaîne  
Type d'accès : lecture seule  
  
 Spécifie si le service prend en charge un thread, plusieurs threads ou les appels réentrants.  
  
### IgnoreExtensionDataObject  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui spécifie s'il faut envoyer des données de sérialisation inconnues sur le câble.  
  
### IncludeExceptionDetailInFaults  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 En cas d'activation, des détails au sujet des exceptions levées sur le rappel sont joints aux erreurs retournées au service.  
  
### MaxItemsInObjectGraph  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Nombre maximal d'éléments autorisés dans un objet sérialisé.  
  
### UseSynchronizationContext  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie s'il faut utiliser le contexte de synchronisation actuel pour choisir le thread d'exécution.  
  
### ValidateMustUnderstand  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie si le système ou l'application applique le traitement d'en\-tête SOAP MustUnderstand.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Namespace|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>