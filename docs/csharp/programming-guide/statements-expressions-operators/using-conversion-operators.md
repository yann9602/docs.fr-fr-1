---
title: "Utilisation d'opérateurs de conversion (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2561b680da567623b8dab13e9e5294c3dd2c1012
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-conversion-operators-c-programming-guide"></a>Utilisation d'opérateurs de conversion (Guide de programmation C#)
Vous pouvez utiliser des opérateurs de conversion `implicit`, qui sont plus faciles à utiliser, ou des opérateurs de conversion `explicit`, qui indiquent clairement à toute personne lisant le code que vous convertissez un type. Cette rubrique illustre les deux types d’opérateurs de conversion.  
  
> [!NOTE]
>  Pour plus d’informations sur les conversions de types simples, consultez [Guide pratique pour convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Guide pratique pour convertir un tableau d’octets en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) ou <xref:System.Convert>.  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’opérateur de conversion explicite. Cet opérateur convertit le type <xref:System.Byte> en un type valeur appelé `Digit`. Étant donné que tous les octets ne pouvant pas être convertis en un chiffre, la conversion est explicite, ce qui signifie qu’un cast doit être utilisé, comme indiqué dans la méthode `Main`.  
  
 [!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un opérateur de conversion implicite en définissant un opérateur de conversion qui annule ce que l’exemple précédent a fait : il effectue une conversion d’une classe de valeur appelée `Digit` en type <xref:System.Byte> intégral. Étant donné que tout chiffre peut être converti en <xref:System.Byte>, il n’est pas nécessaire de forcer les utilisateurs à être explicites à propos de la conversion.  
  
 [!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [is](../../../csharp/language-reference/keywords/is.md)

