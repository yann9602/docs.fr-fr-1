---
title: "Out (modificateur générique) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a>Out (modificateur générique) (Visual Basic)
Paramètres de type générique, la `Out` (mot clé) Spécifie que le type est covariant.  
  
## <a name="remarks"></a>Notes  
 La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.  
  
 Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Règles  
 Vous pouvez utiliser le mot clé `Out` dans les interfaces et délégués génériques.  
  
 Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :  
  
-   Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle. Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué. Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.  
  
 Dans un délégué générique, un paramètre de type peut être déclaré covariant s’il est utilisé uniquement comme un type de retour de méthode et pas utilisé pour les arguments de méthode.  
  
 La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.  
  
 En Visual Basic, vous ne pouvez pas déclarer des événements des interfaces covariants sans spécifier le type délégué. En outre, les interfaces covariants ne peut pas avoir de classes, d’enums ou de structures imbriqués, mais ont des interfaces imbriquées.  
  
## <a name="behavior"></a>Comportement  
 Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type. Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerabe(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.  
  
 Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant. Il montre également comment vous pouvez utiliser la conversion implicite pour les types délégués.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
