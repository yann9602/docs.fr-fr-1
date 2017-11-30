---
title: "Comment : réduire et masquer des sections de code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a31f0c8af9b84e87ebe1e5191d72d19be8340f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Comment : réduire et masquer des sections de code (Visual Basic)
Le `#Region` directive vous permet de réduire et masquer des sections de code dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fichiers. Le `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] éditeur de code. La possibilité de masquer le code de manière sélective rend vos fichiers plus gérable et plus facile à lire. Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).  
  
 `#Region`directives prennent en charge une sémantique de bloc de code comme `#If...#End If`. Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer par une autre ; le début et fin doivent être dans le même bloc. `#Region`directives ne sont pas pris en charge dans les fonctions.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Pour réduire et masquer une section de code  
  
-   Placez la section de code entre les `#Region` et `#End Region` instructions, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code ; par conséquent, les utilisateurs peuvent définir leurs propres blocs de procédures et des classes qui peuvent, à son tour, être réduits. `#Region`les blocs peuvent également être imbriqués dans d’autres `#Region` blocs.  
  
    > [!NOTE]
    >  Masquage du code n’empêche pas sa compilation et n’affecte pas `#If...#End If` instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Mode Plan](/visualstudio/ide/outlining)
