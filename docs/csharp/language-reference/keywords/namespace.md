---
title: "namespace (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a>namespace (référence C#)
Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes. Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Remarques  
 Dans un espace de noms, vous pouvez déclarer un ou plusieurs des types suivants :  
  
-   autre espace de noms  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#. Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier. Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.  
  
 Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable. Consultez [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.  
  
 Il est possible de définir un espace de noms dans deux déclarations ou plus. Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 Pour plus d’informations sur l’utilisation des espaces de noms, consultez les rubriques suivantes :  
  
-   [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Utilisation d’espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Guide pratique pour utiliser l’alias d’espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using](../../../csharp/language-reference/keywords/using.md)
