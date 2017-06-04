---
title: "AsymmetricSecurityBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## Syntaxe  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## Méthodes  
 La classe AsymmetricSecurityBindingElement ne définit pas de méthodes.  
  
## Propriétés  
 La classe AsymmetricSecurityBindingElement a les propriétés suivantes :  
  
### MessageProtectionOrder  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Ordre de chiffrement et de signature des messages de cette liaison.  
  
### RequireSignatureConfirmation  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Si la liaison requiert la confirmation de signature.  
  
## Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>