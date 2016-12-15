---
title: "#Region Directive | Microsoft Docs"
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
  - "vb.Region"
  - "vb.#Region"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic compiler, compiler directives"
  - "#region directive"
  - "region directive (#region)"
  - "#Region keyword"
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #Region Directive
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Réduit et masque des sections de code dans des fichiers Visual Basic.  
  
## Syntaxe  
  
```  
  
        #Region "identifier_string"  
#End Region  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`identifier_string`|Obligatoire.  Chaîne qui joue le rôle du titre d'une région quand elle est réduite.  Les régions sont réduites par défaut.|  
|`#End Region`|Met fin au bloc `#Region`.|  
  
## Notes  
 Utilisez la directive `#Region` pour spécifier un bloc de code que vous pouvez développer ou réduire dans le mode Plan de l'éditeur de code Visual Studio.  Vous pouvez placer, ou *imbriquer*, des régions dans d'autres régions pour grouper des régions semblables.  
  
## Exemple  
 Cet exemple utilise la directive `#Region`.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Mode Plan](/visual-studio/ide/outlining)   
 [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)