---
title: "out (modificateur g&#233;n&#233;rique) (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "covariance, out (mot clé C#)"
  - "out (mot clé C#)"
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# out (modificateur g&#233;n&#233;rique) (R&#233;f&#233;rence C#)
Pour les paramètres de type générique, le mot clé `out` spécifie que le paramètre de type est covariant.  Vous pouvez utiliser le mot clé `out` dans les interfaces et les délégués génériques.  
  
 La covariance vous permet d'utiliser un type plus dérivé que celui spécifié par le paramètre générique.  Cela permet la conversion implicite des classes qui implémentent des interfaces variantes et la conversion implicite des types délégués.  La covariance et la contravariance sont prises en charge pour les types référence mais pas pour les types valeur.  
  
 Une interface ayant un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type.  Par exemple, comme dans .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet de type `IEnumerabe(Of String)` à un objet de type `IEnumerable(Of Object)` sans utiliser des méthodes de conversion spéciales.  
  
 Un autre délégué du même type peut être assigné à un délégué covariant, mais avec un paramètre de type générique plus dérivé.  
  
 Pour plus d'informations, consultez [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemple  
 L'exemple suivant indique comment déclarer, étendre et implémenter une interface générique covariante.  Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.  
  
 [!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Dans une interface générique, un paramètre de type peut être déclaré covariant s'il satisfait aux conditions suivantes :  
  
-   Le paramètre de type est utilisé uniquement comme type de retour de méthodes d'interface et non comme type d'arguments de méthode.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle.  Si dans une interface covariante vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué.  Pour plus d'informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md) et [Utilisation de la variance pour les délégués génériques Func et Action](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).  
  
-   Le paramètre de type n'est pas utilisé comme contrainte générique pour les méthodes d'interface.  
  
## Exemple  
 L'exemple suivant indique comment déclarer, instancier et appeler un délégué générique covariant.  Il indique également comment convertir implicitement des types délégués.  
  
 [!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Dans un délégué générique, un type peut être déclaré covariant s'il est utilisé uniquement comme un type de retour de méthode et n'est pas utilisé pour les arguments de méthode.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Variance dans les interfaces génériques](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)