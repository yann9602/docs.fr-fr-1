---
title: "Contract | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Contract
Contract  
  
## Syntaxe  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## Méthodes  
 La classe Contract ne définit pas de méthodes.  
  
## Propriétés  
 La classe Contract a les propriétés suivantes :  
  
### AppDomainId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID du domaine d'application qui héberge le contrat.  
  
### Behaviors  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Comportements associés à ce contrat.  
  
### Name  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom du contrat dans WSDL.  
  
### Namespace  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Espace de noms de l'élément `portType` dans WSDL.  
  
### Operations  
 Type de données : tableau d'opérations  
  
 Type d'accès : lecture seule  
  
 Opérations de ce contrat.  
  
### ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID du processus qui héberge le contrat.  
  
### ref  
 Type de données: contrat  
  
 Type d'accès : lecture seule  
  
 Type de rappel lorsque le contrat est un contrat duplex.  
  
### SessionMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.  
  
### Type  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type du contrat.  
  
## Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Namespace|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ContractDescription>