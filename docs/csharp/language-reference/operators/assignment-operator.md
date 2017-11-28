---
title: "=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =_CSharpKeyword
helpviewer_keywords: = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>=, opérateur (référence C#)
L’opérateur d’assignation (`=`) stocke la valeur de l’opérande de droite dans l’emplacement de stockage, la propriété ou l’indexeur indiqué par l’opérande de gauche et retourne la valeur comme résultat. Les opérandes doivent être du même type (ou l’opérande de droite doit être implicitement convertible en type de l’opérande de gauche).  
  
## <a name="remarks"></a>Remarques  
 L’opérateur d’assignation ne peut pas être surchargé. Toutefois, vous pouvez définir des opérateurs de conversion implicites pour un type, qui vous permettent d’utiliser l’opérateur d’assignation avec ces types. Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
