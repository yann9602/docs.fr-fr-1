---
title: "Nom de «&lt;nom&gt;&quot; n’est pas déclaré | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
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
ms.openlocfilehash: 81b6862a7f8ceb7998b2ea53336ed3af46b1db5f
ms.lasthandoff: 03/13/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nom de «&lt;nom&gt;' n’est pas déclaré
Une instruction fait référence à un élément de programmation, mais le compilateur ne peut pas trouver un élément portant ce nom exact.  
  
 **ID d’erreur :** BC30451  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du nom dans l’instruction de référence. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]respecte la casse, mais toute autre variation dans l’orthographe est considérée comme un nom complètement différent. Notez que le caractère de soulignement (`_`) fait partie du nom et donc de l’orthographe.  
  
2.  Vérifiez que vous disposez de l’opérateur d’accès aux membres (`.`) entre un objet et son membre. Par exemple, si vous avez un <xref:System.Windows.Forms.TextBox>contrôle nommé `TextBox1`, pour accéder à ses <xref:System.Windows.Forms.TextBoxBase.Text%2A>propriété, vous devez taper `TextBox1.Text`.</xref:System.Windows.Forms.TextBoxBase.Text%2A> </xref:System.Windows.Forms.TextBox> Si, au lieu de cela, vous tapez `TextBox1Text`, vous créez un nom différent.  
  
3.  Si l’orthographe est correcte et que la syntaxe n’importe quel objet d’accès de membre est correcte, vérifiez que l’élément a été déclaré. Pour plus d’informations, consultez [éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Si l’élément de programmation a été déclaré, vérifiez qu’il est dans la portée. Si l’instruction de référence est en dehors de la région qui déclare l’élément de programmation, vous devrez peut-être qualifier le nom de l’élément. Pour plus d’informations, consultez [portée dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des déclarations et des constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
