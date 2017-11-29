---
title: "Utilisation d'opérateurs de conversion (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a43332df795d853c3060a604360adeaea5e3fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-conversion-operators-c-programming-guide"></a>Utilisation d'opérateurs de conversion (Guide de programmation C#)
Vous pouvez utiliser des opérateurs de conversion `implicit`, qui sont plus faciles à utiliser, ou des opérateurs de conversion `explicit`, qui indiquent clairement à toute personne lisant le code que vous convertissez un type. Cette rubrique illustre les deux types d’opérateurs de conversion.  
  
> [!NOTE]
>  Pour plus d’informations sur les conversions de types simples, consultez [Guide pratique pour convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Guide pratique pour convertir un tableau d’octets en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) ou <xref:System.Convert>.  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’opérateur de conversion explicite. Cet opérateur convertit le type <xref:System.Byte> en un type valeur appelé `Digit`. Étant donné que tous les octets ne pouvant pas être convertis en un chiffre, la conversion est explicite, ce qui signifie qu’un cast doit être utilisé, comme indiqué dans la méthode `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un opérateur de conversion implicite en définissant un opérateur de conversion qui annule ce que l’exemple précédent a fait : il effectue une conversion d’une classe de valeur appelée `Digit` en type <xref:System.Byte> intégral. Étant donné que tout chiffre peut être converti en <xref:System.Byte>, il n’est pas nécessaire de forcer les utilisateurs à être explicites à propos de la conversion.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [is](../../../csharp/language-reference/keywords/is.md)
