---
title: "«&lt;elementname&gt;&quot; est obsolète (avertissement Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: ccec3b2659502c84dd4db9c9c4d796362958030b
ms.lasthandoff: 03/13/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>«&lt;elementname&gt;' est obsolète (avertissement Visual Basic)
Une instruction essaie d’accéder à un élément de programmation qui a été marqué avec la <xref:System.ObsoleteAttribute>attribut et la directive pour le traiter comme un avertissement.</xref:System.ObsoleteAttribute>  
  
 Vous pouvez marquer les éléments de programmation comme n’étant plus utilisé par l’application <xref:System.ObsoleteAttribute>à celui-ci.</xref:System.ObsoleteAttribute> Si vous procédez ainsi, vous pouvez définir l’attribut <xref:System.ObsoleteAttribute.IsError%2A>propriété `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A> Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 Par défaut, ce message est un avertissement, car la <xref:System.ObsoleteAttribute.IsError%2A>propriété du <xref:System.ObsoleteAttribute>est `False`.</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A> Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40008  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que le nom de l’élément est orthographié correctement dans la référence du code source.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)

