---
title: "Module &lt;keyword&gt; (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ModuleAttribute"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Module keyword"
  - "Module modifier"
  - "attribute blocks, Module keyword"
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Module &lt;keyword&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'un attribut au début d'un fichier source s'applique au module d'assembly actuel.  
  
## Notes  
 Beaucoup d'attributs appartiennent à un élément de programmation, tel qu'une classe ou une propriété.  Vous appliquez ce type d'attribut en liant le bloc d'attributs, entre les signes "inférieur à" et "supérieur à" \(`< >`\), directement à l'instruction de déclaration.  
  
 Si un attribut n'appartient pas uniquement à l'élément suivant, mais aussi à l'assembly actuel, placez le bloc d'attributs au début du fichier source et identifiez l'attribut avec le mot clé `Module`.  S'il s'applique à l'intégralité de l'assembly, utilisez le mot clé [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md).  
  
 Le modificateur `Module` est différent de l'instruction du même nom \([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)\).  
  
## Voir aussi  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)