---
title: "ServiceToEndpointAssociation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceToEndpointAssociation
Mappe un service à un point de terminaison.  
  
## Syntaxe  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## Méthodes  
 La classe ServiceToEndpointAssociation ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceToEndpointAssociation a les propriétés suivantes :  
  
### ref  
 Type de données : service  
  
 Type d'accès : lecture seule  
Qualificateurs : clé  
  
 Service associé au point de terminaison.  
  
### ref  
 Type de données : point de terminaison  
  
 Type d'accès : lecture seule  
Qualificateurs : clé  
  
 Point de terminaison associé au service.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|