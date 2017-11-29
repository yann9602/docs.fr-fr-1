---
title: "Nom de &#39; &lt;nom&gt;&#39; n’est pas déclaré"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords: BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a63ae74c7179d71756e2b9b4bf6b41a71ce12a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nom de &#39; &lt;nom&gt;&#39; n’est pas déclaré
Une instruction fait référence à un élément de programmation, mais le compilateur ne peut pas trouver un élément portant ce nom exact.  
  
 **ID d’erreur :** BC30451  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du nom dans l’instruction de référence. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]respecte la casse, mais toute autre variation dans l’orthographe est considérée comme un nom complètement différent. Notez que le caractère de soulignement (`_`) fait partie du nom et donc de l’orthographe.  
  
2.  Vérifiez que vous disposez de l’opérateur d’accès au membre (`.`) entre un objet et son membre. Par exemple, si vous disposez d’un contrôle <xref:System.Windows.Forms.TextBox> dont le nom est `TextBox1`, pour accéder à sa propriété <xref:System.Windows.Forms.TextBoxBase.Text%2A> , vous devez taper `TextBox1.Text`. Si, au lieu de cela, vous tapez `TextBox1Text`, vous créez un nom différent.  
  
3.  Si l’orthographe est correcte et que la syntaxe de n’importe quel objet d’accès de membre est correcte, vérifiez que l’élément a été déclaré. Pour plus d’informations, consultez [déclaré les éléments](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Si l’élément de programmation a été déclaré, vérifiez qu’il est dans la portée. Si l’instruction de référence est en dehors de la région déclarant l’élément de programmation, vous devrez peut-être qualifier le nom de l’élément. Pour plus d’informations, consultez [étendue en Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des déclarations et des constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
