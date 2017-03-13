---
title: "Out (Generic Modifier) (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.VarianceOut"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Out keyword [Visual Basic]"
  - "covariance, Out keyword [Visual Basic]"
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Out (Generic Modifier) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Pour les paramètres de type générique, le mot clé `Out` spécifie que le type est covariant.  
  
## Notes  
 La covariance vous permet d'utiliser un type plus dérivé que celui spécifié par le paramètre générique.  Cela permet la conversion implicite des classes qui implémentent des interfaces variantes et la conversion implicite des types délégués.  
  
 Pour plus d'informations, consultez [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Règles  
 Vous pouvez utiliser le mot clé `Out` dans les interfaces et les délégués génériques.  
  
 Dans une interface générique, un paramètre de type peut être déclaré covariant s'il satisfait aux conditions suivantes :  
  
-   Le paramètre de type est utilisé uniquement comme type de retour de méthodes d'interface et non comme type d'arguments de méthode.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle.  Si dans une interface covariante vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué.  Pour plus d'informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md) et [Utilisation de la variance pour les délégués génériques Func et Action](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).  
  
-   Le paramètre de type n'est pas utilisé comme contrainte générique pour les méthodes d'interface.  
  
 Dans un délégué générique, un paramètre de type peut être déclaré covariant s'il est utilisé uniquement comme type de retour de méthode et non pour les arguments de méthode.  
  
 La covariance et la contravariance sont prises en charge pour les types référence mais pas pour les types valeur.  
  
 En Visual Basic, vous ne pouvez pas déclarer d'événements dans des interfaces covariantes sans spécifier le type délégué.  De même, les interfaces covariantes ne peuvent pas avoir de classes, d'enums ou de structures imbriqués, mais elles peuvent inclure des interfaces imbriquées.  
  
## Comportement  
 Une interface ayant un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type.  Par exemple, comme dans .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet de type `IEnumerabe(Of String)` à un objet de type `IEnumerable(Of Object)` sans utiliser des méthodes de conversion spéciales.  
  
 Un autre délégué du même type peut être assigné à un délégué covariant, mais avec un paramètre de type générique plus dérivé.  
  
## Exemple  
 L'exemple suivant indique comment déclarer, étendre et implémenter une interface générique covariante.  Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## Exemple  
 L'exemple suivant indique comment déclarer, instancier et appeler un délégué générique covariant.  Il montre également comment vous pouvez utiliser la conversion implicite pour les types délégués.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## Voir aussi  
 [Variance dans les interfaces génériques](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)