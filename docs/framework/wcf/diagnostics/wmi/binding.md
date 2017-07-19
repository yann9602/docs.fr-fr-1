---
title: "Liaison | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Liaison
WMI Binding  
  
## Syntaxe  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## Méthodes  
 La classe Binding ne définit pas de méthodes.  
  
## Propriétés  
 La classe Binding a les propriétés suivantes :  
  
### BindingElement  
 Type de données : tableau BindingElement  
  
 Type d'accès : lecture seule  
  
 Collection d'éléments de liaison implémentés par la liaison.  
  
### CloseTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle de temps spécifié pour l'exécution d'une opération de fermeture.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de la liaison.  
  
### Espace de noms  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Espace de noms XML de la liaison.  
  
### OpenTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle de temps spécifié pour l'exécution d'une opération d'ouverture.  
  
### ReceiveTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle de temps spécifié pour l'exécution d'une opération de réception.  
  
### Scheme  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Modèle de transport URI utilisé par les fabrications et écouteurs de canal construits par la liaison.  
  
### SendTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle de temps spécifié pour l'exécution d'une opération d'envoi.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.Binding>