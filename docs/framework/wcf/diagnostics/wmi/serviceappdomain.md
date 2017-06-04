---
title: "ServiceAppDomain | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceAppDomain
Mappe un service à un domaine d'application.  
  
## Syntaxe  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## Méthodes  
 La classe ServiceAppDomain ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceAppDomain a les propriétés suivantes :  
  
### ref  
 Type de données : service               
 Qualificateurs : clé  
  
 Type d'accès : lecture seule  
  
 Service de ce domaine d'application.  
  
### ref  
 Type de données : AppDomainInfo               
 Qualificateurs : clé  
  
 Type d'accès : lecture seule  
  
 Contient des propriétés du domaine d'application.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|