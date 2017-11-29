---
title: "Interroger une collection d’objets"
description: Comment interroger les collections.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="query-a-collection-of-objects"></a>Interroger une collection d’objets
Cet exemple montre comment effectuer une requête simple sur une liste d’objets `Student`. Chaque objet `Student` contient des informations de base sur l’étudiant et une liste qui représente les notes de l’étudiant lors de quatre examens.  
  
 Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students`.  
  
## <a name="example"></a>Exemple  
 La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Cette requête est volontairement simple pour vous permettre de faire des essais. Par exemple, vous pouvez essayer plus de conditions dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.  
  

## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)  
 [Chaînes interpolées](../language-reference/keywords/interpolated-strings.md)
