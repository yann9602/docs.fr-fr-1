---
title: "checked (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5826c8e6f99352c730824bb504a168226b9e6600
ms.lasthandoff: 03/13/2017

---
# <a name="checked-c-reference"></a>checked (référence C#)
Le mot clé `checked` permet d’activer explicitement le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.  
  
 Par défaut, une expression qui contient uniquement des valeurs constantes provoque une erreur du compilateur si l’expression produit une valeur située en dehors de la plage du type de destination. Si l’expression contient une ou plusieurs valeurs non constantes, le compilateur ne détecte pas le dépassement de capacité. L’évaluation de l’expression assignée à `i2` dans l’exemple suivant ne provoque pas d’erreur du compilateur.  
  
 [!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Par défaut, ces expressions non constantes ne font pas l’objet d’une vérification d’un dépassement de capacité au moment de l’exécution et ne lèvent aucune exception de dépassement de capacité. L’exemple précédent affiche -2 147 483 639 comme somme de deux entiers positifs.  
  
 Le contrôle de dépassement de capacité peut être activé par les options du compilateur, la configuration de l’environnement ou l’utilisation du mot clé `checked`. Les exemples suivants montrent comment utiliser une expression `checked` ou un bloc `checked` pour détecter le dépassement de capacité produit par la somme précédente au moment de l’exécution. Les deux exemples lèvent une exception de dépassement de capacité.  
  
 [!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 Vous pouvez utiliser le mot clé [unchecked](../../../csharp/language-reference/keywords/unchecked.md) pour empêcher la vérification du dépassement de capacité.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser `checked` pour activer la vérification du dépassement de capacité au moment de l’exécution.  
  
 [!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
