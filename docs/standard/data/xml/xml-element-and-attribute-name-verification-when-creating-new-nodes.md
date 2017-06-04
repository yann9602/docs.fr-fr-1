---
title: "V&#233;rification des noms d&#39;attribut et d&#39;&#233;l&#233;ment XML lors de la cr&#233;ation de nœuds | Microsoft Docs"
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
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# V&#233;rification des noms d&#39;attribut et d&#39;&#233;l&#233;ment XML lors de la cr&#233;ation de nœuds
Le DOM \(Document Object Model\) XML contrôle la validité des noms lors de la création de nœuds d'élément ou d'attribut.  Si ces noms contiennent des caractères non conformes, une exception est levée.  Pour être certain que les noms sont valides et encodés correctement, vous devez recourir à la classe **XmlConvert** pour encoder le nom et le décoder à nouveau au niveau de l'application.  **XmlWriter** possède des méthodes qui effectuent des opérations supplémentaires afin de garantir un format correct pour le code XML qui est généré.  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)