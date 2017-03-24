---
title: "Type sous-jacent &lt;typename&gt; d’Enum n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
dev_langs:
- VB
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 8
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
ms.openlocfilehash: 51f9c520922260f6d38cf170f46f9c4d88ed4028
ms.lasthandoff: 03/13/2017

---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Type sous-jacent &lt;typename&gt; d’Enum n’est pas conforme CLS
Type de données spécifié pour cette énumération n’est pas inclus dans le [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS). Ce n’est pas une erreur dans votre composant, parce que le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prennent en charge ce type de données. Toutefois, un autre composant écrit dans le code strictement conforme CLS ne prenne pas en charge ce type de données. Ce composant n’est peut-être pas en mesure d’interagir correctement avec votre composant.  
  
 Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte (type de données)](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong (type de données)](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort (type de données)](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40032  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si votre composant sert d’interface uniquement avec d’autres [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] composants ou n’envoie pas d’interface avec d’autres composants, vous ne devez pas modifier quoi que ce soit.  
  
-   Si vous utilisez un composant non écrit pour le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], vous pouvez déterminer, par réflexion ou à partir de la documentation, s’il prend en charge ce type de données. Si c’est le cas, il est inutile de modifier quoi que ce soit.  
  
-   Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Par exemple, `uint` correspond souvent à 16 bits dans d’autres environnements. Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que `UShort` au lieu de `UInteger` dans votre [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.  
  
## <a name="see-also"></a>Voir aussi  
 [Réflexion](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Réflexion](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)   
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
