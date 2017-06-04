---
title: "CustomBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# CustomBindingElement
CustomBindingElement  
  
## Syntaxe  
  
```  
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## Méthodes  
 La classe CustomBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe CustomBindingElement possède la propriété suivante :  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Chaîne qui contient le nom de configuration de la liaison.  Cette valeur est une chaîne définie par l'utilisateur qui sert de chaîne d'identification à la liaison personnalisée.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.CustomBinding>