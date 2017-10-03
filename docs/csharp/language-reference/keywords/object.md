---
title: "object (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 744debc51f68cc52f03bce09c9f276a66ae085e1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="object-c-reference"></a>object (référence C#)
Le type `object` est un alias du type <xref:System.Object> du .NET Framework. Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>. Vous pouvez assigner des valeurs de tout type aux variables de type `object`. Quand une variable d’un type valeur est convertie en type objet, elle est dite *boxed*. Quand une variable de type objet est convertie en type valeur, elle est dite *unboxed*. Pour plus d’informations, consultez [Boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment les variables de type `object` acceptent des valeurs de tout type de données et comment les variables de type `object` utilisent des méthodes d’<xref:System.Object> du .NET Framework.  
  
 [!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)

