---
title: "in (modificateur générique) (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
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
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: 663fa75a7e214ed97efb45dda2c9ac298559653d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="in-generic-modifier-c-reference"></a>in (modificateur générique) (Référence C#)
Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant. Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.  
  
 La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués. La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.  
  
 Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique s’il est utilisé uniquement comme un type d’argument de méthode et non comme un type de retour de méthode. Les paramètres `Ref` et `out` ne peuvent pas être variants.  
  
 Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface. Par exemple, comme dans le .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Employee` hérite de `Person`.  
  
 Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.  
  
 Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.  
  
 [!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant. Il montre également comment convertir implicitement un type délégué.  
  
 [!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)   
 [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)

