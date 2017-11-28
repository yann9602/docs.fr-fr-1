---
title: "into (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords: into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a>into (Référence C#)
Le mot clé contextuel `into` permet de créer un identificateur temporaire pour stocker les résultats d’une clause [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) ou [select](../../../csharp/language-reference/keywords/select-clause.md) dans un nouvel identificateur. Cet identificateur peut lui-même être un générateur pour d’autres commandes de requête. Quand il est utilisé dans une clause `group` ou `select`, le nouvel identificateur est parfois appelé *continuation*.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` dont le type déduit est `IGrouping`. En utilisant l’identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> dans chaque groupe et sélectionner uniquement les groupes qui contiennent deux mots ou plus.  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 L’utilisation de `into` dans une clause `group` n’est nécessaire que si vous voulez effectuer des opérations de requête supplémentaires dans chaque groupe. Pour plus d’informations, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Pour obtenir un exemple d’utilisation de `into` dans une clause `join`, consultez [join, clause](../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)
