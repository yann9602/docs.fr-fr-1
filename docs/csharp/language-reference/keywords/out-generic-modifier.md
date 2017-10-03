---
title: "out (modificateur générique) (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: 15
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
ms.openlocfilehash: a560a0307723d32750a7e26ad4ee1afec360a849
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="out-generic-modifier-c-reference"></a>out (modificateur générique) (référence C#)
Pour les paramètres de type générique, le mot clé `out` spécifie que le paramètre de type est covariant. Vous pouvez utiliser le mot clé `out` dans les interfaces et délégués génériques.  
  
 La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués. La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.  
  
 Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type. Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerabe(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.  
  
 Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.  
  
 Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.  
  
 [!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :  
  
-   Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle. Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué. Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) et [Utilisation de la variance pour les délégués génériques Func et Action](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).  
  
-   Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant. Il montre également comment convertir implicitement des types délégués.  
  
 [!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Dans un délégué générique, un type peut être déclaré comme étant covariant s’il est utilisé uniquement comme type de retour des méthodes, mais pas pour des arguments de méthode.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)

