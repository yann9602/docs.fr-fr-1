---
title: "XmlDictionaryReaderQuotas | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## Syntaxe  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## Méthodes  
 La classe XmlDictionaryReaderQuotas ne définit aucune méthode.  
  
## Propriétés  
 La classe XmlDictionaryReaderQuotas a les propriétés suivantes :  
  
### MaxArrayLength  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Longueur maximale de tableau autorisée.  
  
### MaxBytesPerRead  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal d'octets pouvant être renvoyés par lecture.  
  
### MaxDepth  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Profondeur maximale de nœud imbriqué par lecture.  
  
### MaxNameTableCharCount  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de caractères autorisés dans un nom de tableau.  
  
### MaxStringContentLength  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de caractères autorisés dans un contenu d'élément XML.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.Xml.XmlDictionaryReaderQuotas>   
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>