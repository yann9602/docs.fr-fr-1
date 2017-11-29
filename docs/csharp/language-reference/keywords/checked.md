---
title: "checked (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords: checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a>checked (référence C#)
Le mot clé `checked` permet d’activer explicitement le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.  
  
 Par défaut, une expression qui contient uniquement des valeurs constantes provoque une erreur du compilateur si l’expression produit une valeur située en dehors de la plage du type de destination. Si l’expression contient une ou plusieurs valeurs non constantes, le compilateur ne détecte pas le dépassement de capacité. L’évaluation de l’expression assignée à `i2` dans l’exemple suivant ne provoque pas d’erreur du compilateur.  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Par défaut, ces expressions non constantes ne font pas l’objet d’une vérification d’un dépassement de capacité au moment de l’exécution et ne lèvent aucune exception de dépassement de capacité. L’exemple précédent affiche -2 147 483 639 comme somme de deux entiers positifs.  
  
 Le contrôle de dépassement de capacité peut être activé par les options du compilateur, la configuration de l’environnement ou l’utilisation du mot clé `checked`. Les exemples suivants montrent comment utiliser une expression `checked` ou un bloc `checked` pour détecter le dépassement de capacité produit par la somme précédente au moment de l’exécution. Les deux exemples lèvent une exception de dépassement de capacité.  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 Vous pouvez utiliser le mot clé [unchecked](../../../csharp/language-reference/keywords/unchecked.md) pour empêcher la vérification du dépassement de capacité.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser `checked` pour activer la vérification du dépassement de capacité au moment de l’exécution.  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
