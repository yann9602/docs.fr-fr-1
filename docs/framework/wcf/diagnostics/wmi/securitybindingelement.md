---
title: "SecurityBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# SecurityBindingElement
SecurityBindingElement  
  
## Syntaxe  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## Méthodes  
 La classe SecurityBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe SecurityBindingElement a les propriétés suivantes :  
  
### DefaultAlgorithmSuite  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie les algorithmes à utiliser avec la liaison.  
  
### IncludeTimestamp  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si chaque message contient un horodatage.  
  
### KeyEntropyMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Source d'entropie utilisée pour créer des clés.  
  
### LocalServiceSecuritySettings  
 Type de données : LocalServiceSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Propriétés de sécurité spécifiques d'une liaison pour le service local..  
  
### MessageSecurityVersion  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Version utilisée pour la sécurité de message.  
  
### SecurityHeaderLayout  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Ordre des éléments dans l'en\-tête de sécurité pour cette liaison.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>