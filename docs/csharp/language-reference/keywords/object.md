---
title: "object (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords: object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a>object (référence C#)
Le type `object` est un alias du type <xref:System.Object> du .NET Framework. Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>. Vous pouvez assigner des valeurs de tout type aux variables de type `object`. Quand une variable d’un type valeur est convertie en type objet, elle est dite *boxed*. Quand une variable de type objet est convertie en type valeur, elle est dite *unboxed*. Pour plus d’informations, consultez [Boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment les variables de type `object` acceptent des valeurs de tout type de données et comment les variables de type `object` utilisent des méthodes d’<xref:System.Object> du .NET Framework.  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)
