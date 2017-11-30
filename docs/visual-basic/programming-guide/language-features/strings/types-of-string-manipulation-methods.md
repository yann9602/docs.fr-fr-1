---
title: "Types de méthodes de manipulation de chaînes en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Types de méthodes de manipulation de chaînes en Visual Basic
Il existe plusieurs façons différentes pour analyser et manipuler des chaînes. Certaines méthodes font partie de la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] langage et autres sont inhérentes à la `String` classe.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Langage Visual Basic et .NET Framework  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]méthodes sont utilisées en tant que fonctions inhérentes du langage. Ils peuvent être utilisés sans qualification dans votre code. L’exemple suivant illustre une utilisation classique d’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] commande de manipulation de chaînes :  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Dans cet exemple, le `Mid` fonction effectue une opération directe sur `aString` et affecte la valeur à `bString`.  
  
 Pour obtenir la liste des méthodes de manipulation de chaîne Visual Basic, consultez [résumé de Manipulation de chaîne](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Méthodes partagées et des méthodes d’Instance  
 Vous pouvez également manipuler des chaînes avec les méthodes de la `String` classe. Il existe deux types de méthodes de `String`: *partagé* méthodes et *instance* méthodes.  
  
#### <a name="shared-methods"></a>Méthodes partagées  
 Une méthode partagée est une méthode qui provient du `String` classe proprement dit et ne nécessite pas une instance de cette classe. Ces méthodes peuvent être qualifiés avec le nom de la classe (`String`) plutôt qu’avec une instance de la `String` classe. Exemple :  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 Dans l’exemple précédent, le <xref:System.String.Copy%2A?displayProperty=nameWithType> méthode est une méthode statique, qui agit sur une expression qui lui est attribuée et affecte la valeur obtenue dans `bString`.  
  
#### <a name="instance-methods"></a>Méthodes d’instance  
 Méthodes d’instance, en revanche, proviennent d’une instance particulière de `String` et doit être qualifié avec le nom d’instance. Exemple :  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Dans cet exemple, le <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode est une méthode de l’instance de `String` (autrement dit, `aString`). Il effectue une opération sur `aString` et assigne la valeur à `bString`.  
  
 Pour plus d’informations, consultez la documentation relative à la <xref:System.String> classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
