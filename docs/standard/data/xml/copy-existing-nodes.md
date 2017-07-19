---
title: "Copie de nœuds existants | Microsoft Docs"
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
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Copie de nœuds existants
Le DOM \(Document Object Model\) XML comporte de nombreuses méthodes et propriétés que vous pouvez utiliser pour sélectionner un nœud, par exemple **SelectSingleNode**, **ChildNodes\[int i\]** ou **Attributes\[int i\]**.  Une fois le nœud sélectionné, vous pouvez l'insérer dans l'arborescence à l'aide de l'une des méthodes d'insertion adaptées à ce type de nœud particulier.  La seule restriction à l'insertion d'un nœud dans l'arborescence est que cette opération ne doit pas compromettre la validité du format du document.  Quand un nœud existant est inséré dans l'arborescence DOM, il est supprimé de sa position d'origine et ajouté à sa position de destination.  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)