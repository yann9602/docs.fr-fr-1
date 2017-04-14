---
title: "MtomMessageEncodingBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## Syntaxe  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## Méthodes  
 La classe MtomMessageEncodingBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe MtomMessageEncodingBindingElement a les propriétés suivantes :  
  
### Encodage  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  
  
### MaxReadPoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  
  
### MaxWritePoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  
  
### ReaderQuotas  
 Type de données : XmlDictionaryReaderQuotas  
  
 Type d'accès : lecture seule  
  
 Quotas des lecteurs.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>