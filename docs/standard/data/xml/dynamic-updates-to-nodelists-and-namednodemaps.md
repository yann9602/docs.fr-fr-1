---
title: "Mises &#224; jour dynamiques de NodeList et NamedNodeMap | Microsoft Docs"
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
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Mises &#224; jour dynamiques de NodeList et NamedNodeMap
Dans la mesure où **XmlNodeList** et **XmlNamedNodeMap** contiennent une collection de nœuds, mais où le document XML est chargé en mémoire et est modifié, le World Wide Web Consortium \(W3C\) établit que ces objets contenant des collections de nœuds doivent être dynamiques.  Dès lors, si le document sous\-jacent change, les données figurant dans ces deux objets doivent changer également.  C'est pourquoi, si vous avez un **XmlNodeList** contenant tous les éléments enfants d'un élément particulier \(par exemple, l'élément X\), vous ajoutez un élément supplémentaire, l'élément Q, au document sous l'élément X.  Le **XmlNodeList** doit également avoir le nouvel élément Q ajouté à sa collection.  L'inverse est vrai également.  Si un nœud est ajouté à **XmlNodeList**, le document sous\-jacent est mis à jour en conséquence.  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)