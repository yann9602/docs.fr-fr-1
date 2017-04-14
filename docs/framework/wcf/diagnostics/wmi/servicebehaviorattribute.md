---
title: "ServiceBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## Syntaxe  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## Méthodes  
 La classe ServiceBehaviorAttribute ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceBehaviorAttribute a les propriétés suivantes :  
  
### AutomaticSessionShutdown  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique s'il faut fermer automatiquement une session lorsqu'un client ferme une session de sortie.  
  
### ConcurrencyMode  
 Type de données : chaîne  
Type d'accès : lecture seule  
  
 Indique si un service prend en charge un thread, plusieurs threads ou des appels réentrants.  
  
### ConfigurationName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de la configuration du service.  
  
### IgnoreExtensionDataObject  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie s'il faut envoyer des données de sérialisation inconnues sur le câble.  
  
### IncludeExceptionDetailInFaults  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie s'il convient d'inclure des informations d'exception gérées dans les détails des fautes SOAP renvoyées aux clients à des fins de débogage.  
  
### InstanceContextMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie quand un nouvel objet de service est créé.  
  
### MaxItemsInObjectGraph  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal d'éléments autorisés dans un objet sérialisé.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Attribut de nom du service dans WSDL.  
  
### Espace de noms  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Espace de noms cible du service dans WSDL.  
  
### ReleaseServiceInstanceOnTransactionComplete  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie si l'objet de service est recyclé lorsque la transaction actuelle se termine.  
  
### TransactionAutoCompleteOnSessionClose  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie si les transactions en attente sont complétées lorsque la session actuelle se ferme.  
  
### TransactionIsolationLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie le niveau d'isolation de la transaction.  
  
### TransactionTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période pendant laquelle une transaction doit s'effectuer.  
  
### UseSynchronizationContext  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie s'il faut utiliser le contexte de synchronisation actuel pour choisir l'exécution d'un thread.  
  
### ValidateMustUnderstand  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie si le système ou l'application applique le traitement d'en\-tête SOAP MustUnderstand.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Namespace|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>