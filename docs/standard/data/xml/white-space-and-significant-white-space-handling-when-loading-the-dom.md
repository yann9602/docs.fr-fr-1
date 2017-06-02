---
title: "Gestion des espaces blancs significatifs ou non lors du chargement du DOM | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Gestion des espaces blancs significatifs ou non lors du chargement du DOM
Lors du chargement du document, vous pouvez définir une option qui préserve les espaces blancs et crée des nœuds **XmlWhitespace** dans l'arborescence du document.  Pour créer des nœuds d'espaces blancs, attribuez la valeur true à la propriété **PreserveWhitespace**.  Si cette propriété a pour valeur **false** \(la valeur par défaut\), les nœuds d'espaces blancs ne sont pas créés.  Les nœuds d'espaces blancs significatifs sont toujours préservés et des nœuds **XmlSignificantWhitespace** sont toujours créés en mémoire pour représenter ces données, quelle que soit la valeur de l'indicateur **PreserveWhitespace**.  
  
 Si le document est chargé à partir d'un lecteur, la définition de la propriété d'indicateur **PreserveWhitespace** sur la classe **XmlDocument** affecte la création de nœuds **XmlWhitespace** uniquement lorsque la propriété **WhitespaceHandling** sur le **XmlTextReader** n'a pas la valeur **WhitespaceHandling.None**.  C'est la valeur de la propriété **WhitespaceHandling** sur le lecteur qui prend le pas sur le paramétrage de cet indicateur sur le **XmlDocument**.  Pour plus d'informations sur **XmlSignificantWhitespace**, voir [Classe XmlSignificantWhitespace](frlrfSystemXmlXmlSignificantWhitespaceClassTopic).  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)