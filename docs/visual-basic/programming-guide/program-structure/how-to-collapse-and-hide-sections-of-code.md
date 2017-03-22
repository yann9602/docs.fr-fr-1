---
title: "Comment : réduire et masquer des Sections de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 200a90b6983277d46b6e5c7b27ee4a90ecf88c40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Comment : réduire et masquer des sections de code (Visual Basic)
Le `#Region` directive vous permet de réduire et masquer des sections de code dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fichiers. Le `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] éditeur de code. La possibilité de masquer le code de manière sélective rend vos fichiers plus gérable et plus facile à lire. Pour plus d’informations, voir [Mode Plan](https://docs.microsoft.com/visualstudio/ide/outlining).  
  
 `#Region`directives prennent en charge les sémantiques de bloc de code comme `#If...#End If`. Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer par une autre ; le début et fin doivent être dans le même bloc. `#Region`directives ne sont pas pris en charge dans les fonctions.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Pour réduire et masquer une section de code  
  
-   Placez la section de code entre les `#Region` et `#End Region` instructions, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrConditionalComp n °&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code ; par conséquent, les utilisateurs peuvent définir leurs propres blocs de procédures et des classes qui peuvent, à son tour, être réduits. `#Region`les blocs peuvent également être imbriqués dans les autres `#Region` blocs.  
  
    > [!NOTE]
    >  Masquage du code n’empêche pas sa compilation et n’affecte pas `#If...#End If` instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Mode Plan](https://docs.microsoft.com/visualstudio/ide/outlining)
