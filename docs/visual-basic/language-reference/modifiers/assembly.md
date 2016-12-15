---
title: "Assembly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Assembly"
  - "vb.AssemblyAttribute"
  - "Assembly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Assembly modifier"
  - "Assembly keyword"
  - "attribute blocks, Assembly keyword"
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Assembly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'un attribut s'applique au début d'un fichier source à l'intégralité de l'assembly.  
  
## Notes  
 Beaucoup d'attributs appartiennent à un élément de programmation, tel qu'une classe ou une propriété.  Vous appliquez ce type d'attribut en liant le bloc d'attributs, entre les signes "inférieur à" et "supérieur à" \(`< >`\), directement à l'instruction de déclaration.  
  
 Si un attribut n'appartient pas uniquement à l'élément suivant, mais aussi à l'intégralité de l'assembly, placez le bloc d'attributs au début du fichier source et identifiez l'attribut avec le mot clé `Assembly`.  S'il s'applique au module d'assembly actuel, utilisez le mot clé [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo.vb, auquel cas vous n'êtes pas obligé d'utiliser un bloc d'attributs dans votre fichier de code source principal.  
  
## Voir aussi  
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)