---
title: "Procédures génériques dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a>Procédures génériques dans Visual Basic
A *procédure générique*, également appelé un *méthode générique*, est une procédure définie au moins un paramètre de type. Cela permet au code appelant d’adapter les types de données à ses besoins chaque fois qu’il appelle la procédure.  
  
 Une procédure n’est pas générique simplement en vertu défini à l’intérieur d’une classe générique ou une structure générique. Pour être générique, la procédure doit prendre au moins un paramètre de type, en plus de tous les paramètres normaux que peut prendre. Une classe générique ou une structure peut contenir des procédures non génériques et une classe non générique, structure, ou le module peut contenir des procédures génériques.  
  
 Une procédure générique peut utiliser ses paramètres de type dans sa liste de paramètres normale, dans son type de retour si elle comporte du code et dans sa procédure.  
  
## <a name="type-inference"></a>Inférence de type  
 Vous pouvez appeler une procédure générique sans fournir d’arguments de type du tout. Si vous l’appelez de cette façon, le compilateur tente de déterminer les types de données appropriés à passer aux arguments de type de la procédure. Il s’agit *l’inférence de type*. Le code suivant illustre un appel dans lequel le compilateur déduit qu’il doit passer le type `String` au paramètre de type `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Si le compilateur ne peut pas déduire les arguments de type à partir du contexte de votre appel, il signale une erreur. Une des causes possibles de cette erreur est une incompatibilité de rang de tableau. Par exemple, supposons que vous définissez un paramètre normal comme un tableau d’un paramètre de type. Si vous appelez la procédure générique en fournissant un tableau d’un rang différent (nombre de dimensions), l’incompatibilité provoque l’inférence de type échec. Le code suivant illustre un appel dans lequel un tableau à deux dimensions est passé à une procédure qui attend un tableau unidimensionnel.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Vous pouvez appeler l’inférence de type uniquement en omettant tous les arguments de type. Si vous fournissez un argument de type, vous devez fournir toutes les.  
  
 L’inférence de type est pris en charge uniquement pour les procédures génériques. Vous ne pouvez pas appeler l’inférence de type sur les classes génériques, des structures, des interfaces ou des délégués.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant définit un type générique `Function` procédure pour rechercher un élément particulier dans un tableau. Il définit un paramètre de type et l’utilise pour construire les deux paramètres dans la liste de paramètres.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Commentaires  
 L’exemple précédent nécessite la capacité à comparer `searchValue` sur chaque élément de `searchArray`. Pour garantir cette capacité, il contraint le paramètre de type `T` pour implémenter le <xref:System.IComparable%601> interface. Le code utilise le <xref:System.IComparable%601.CompareTo%2A> méthode au lieu du `=` (opérateur), car il n’existe aucune garantie qu’un argument de type fourni pour `T` prend en charge la `=` opérateur.  
  
 Vous pouvez tester le `findElement` procédure avec le code suivant.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Les appels précédents à `MsgBox` affichent respectivement de « 0 », « 1 » et « -1 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Types génériques en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Guide pratique : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Guide pratique : utiliser une classe générique](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procédures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Paramètres et arguments d’une procédure](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Liste de types](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Liste de paramètres](../../../../visual-basic/language-reference/statements/parameter-list.md)
