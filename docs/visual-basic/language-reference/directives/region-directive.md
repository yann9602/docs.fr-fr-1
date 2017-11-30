---
title: "#<a name=\"region-directive\"></a>Directive de région"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a>#Region, directive
Réduit et masque des sections de code dans des fichiers Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`identifier_string`|Obligatoire. Chaîne qui joue le rôle du titre d'une région quand elle est réduite. Les régions sont réduites par défaut.|  
|`#End Region`|Met fin au bloc `#Region`.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez la directive `#Region` pour spécifier un bloc de code que vous pouvez développer ou réduire dans le mode Plan de l'éditeur de code Visual Studio. Vous pouvez placer, ou *imbriquer*, régions dans d’autres régions pour grouper des régions semblables.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la directive `#Region`.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Mode Plan](/visualstudio/ide/outlining)  
 [Guide pratique : réduire et masquer des sections de code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
