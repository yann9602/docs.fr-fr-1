---
title: "Guide pratique pour rechercher des chaînes à l’aide d’expressions régulières (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fb05d1702c75be8fd224ee0f34d7d8d3fe71f207
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>Guide pratique pour rechercher des chaînes à l’aide d’expressions régulières (Guide de programmation C#)
La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> permet d’effectuer des recherches de chaînes. La complexité de ces recherches peut aller de la plus simple à celle qui exploite au mieux les expressions régulières. Voici deux exemples de recherche de chaînes à l’aide de la classe <xref:System.Text.RegularExpressions.Regex>. Pour plus d’informations, consultez [Expressions régulières .NET Framework](https://msdn.microsoft.com/library/hs600312).  
  
## <a name="example"></a>Exemple  
 Le code suivant est une application console qui effectue une recherche simple non sensible à la casse dans les chaînes d’un tableau. La méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> effectue la recherche en fonction de la chaîne à rechercher et du modèle de recherche. Dans ce cas, un troisième argument est utilisé pour indiquer que la casse doit être ignorée. Pour plus d'informations, consultez <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>Exemple  
 Le code suivant est une application console qui utilise des expressions régulières pour valider le format de chaque chaîne d’un tableau. La validation exige que chaque chaîne prenne la forme d’un numéro de téléphone constitué de trois groupes de chiffres séparés par des tirets, les deux premiers groupes contenant trois chiffres et le troisième contenant quatre chiffres. Cette validation s’appuie sur l’expression régulière `^\\d{3}-\\d{3}-\\d{4}$`. Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [.NET Framework (expressions régulières)](https://msdn.microsoft.com/library/hs600312)   
 [Langage des expressions régulières - Aide-mémoire](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)

