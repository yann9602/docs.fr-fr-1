---
title: "out (modificateur générique) (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25019408387bbf085475482c74a3fc6001321b24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="out-generic-modifier-c-reference"></a>out (modificateur générique) (référence C#)
Pour les paramètres de type générique, le mot clé `out` spécifie que le paramètre de type est covariant. Vous pouvez utiliser le mot clé `out` dans les interfaces et délégués génériques.  
  
 La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués. La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.  
  
 Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type. Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerable(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.  
  
 Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.  
  
 Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :  
  
-   Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle. Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué. Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant. Il montre également comment convertir implicitement des types délégués.  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Dans un délégué générique, un type peut être déclaré comme étant covariant s’il est utilisé uniquement comme type de retour des méthodes, mais pas pour des arguments de méthode.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)
