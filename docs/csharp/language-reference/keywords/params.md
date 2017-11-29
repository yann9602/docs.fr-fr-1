---
title: "params (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66cfc8e7b131a4443ee227df5e39c7e3b775324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="params-c-reference"></a>params (référence C#)
Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](../../../csharp/language-reference/keywords/method-parameters.md) qui prend un nombre variable d’arguments.  
  
 Vous pouvez envoyer une liste séparée par des virgules d’arguments du type spécifié dans la déclaration du paramètre ou envoyer un tableau d’arguments du type spécifié. Vous pouvez aussi ne pas envoyer d’arguments. Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.  
  
 Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)
