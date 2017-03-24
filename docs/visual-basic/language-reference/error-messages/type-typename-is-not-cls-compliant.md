---
title: "Type &lt;typename&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
dev_langs:
- VB
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
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
ms.openlocfilehash: b28ae4ff4a4665040f3e97477d6197065762654a
ms.lasthandoff: 03/13/2017

---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Type &lt;typename&gt; n’est pas conforme CLS
Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.  
  
 Pour une application conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il doit utiliser uniquement des types conformes CLS.  
  
 Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte (type de données)](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong (type de données)](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort (type de données)](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID d’erreur :** BC40041  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si votre application doit être conforme CLS, modifiez le type de données de cet élément au type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si votre application n’a pas besoin être conforme CLS, il est inutile de modifier quoi que ce soit. Vous devez être conscient de sa non-conformité, toutefois.  
  
## <a name="see-also"></a>Voir aussi  
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
