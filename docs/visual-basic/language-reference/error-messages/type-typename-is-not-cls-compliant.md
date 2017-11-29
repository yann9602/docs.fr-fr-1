---
title: "Type &lt;typename&gt; n’est pas conforme CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d45da3b061dff0f82c1155daf5724033261bbdaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Type &lt;typename&gt; n’est pas conforme CLS
Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.  
  
 Une application peut être conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), elle doit utiliser uniquement des types conformes CLS.  
  
 Les types de données [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte (type de données)](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong (type de données)](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort (type de données)](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID d’erreur :** BC40041  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si votre application doit être conforme CLS, modifiez le type de données de cet élément pour le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si votre application n’a pas besoin être conforme CLS, il est inutile d’apporter de modifications. Soyez conscient de sa non-conformité, toutefois.  
  
## <a name="see-also"></a>Voir aussi  
 [\<PAVE sur > écriture d’un Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
