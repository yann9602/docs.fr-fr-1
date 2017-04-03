---
title: "Types énumération (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8c23c17967474af0f91c0dda6d071073234736c6
ms.lasthandoff: 03/13/2017

---
# <a name="enumeration-types-c-programming-guide"></a>Types énumération (Guide de programmation C#)
Un type énumération (également appelé énumération ou enum) offre un moyen efficace de définir un ensemble de constantes intégrales nommées qui peuvent être assignées à une variable. Par exemple, supposez que vous devez définir une variable dont la valeur représente un jour de la semaine. Il n’y a que sept valeurs significatives qui pourront être stockées par cette variable. Pour définir ces valeurs, vous pouvez utiliser un type énumération, qui est déclaré à l’aide du mot clé [enum](../../csharp/language-reference/keywords/enum.md).  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 Par défaut, le type sous-jacent de chaque élément dans l’énumération est [int](../../csharp/language-reference/keywords/int.md). Vous pouvez spécifier un autre type numérique intégral à l’aide d’un signe deux-points, comme illustré dans l’exemple précédent. Pour obtenir une liste complète des types possibles, consultez [enum (référence C#)](../../csharp/language-reference/keywords/enum.md).  
  
 Vous pouvez vérifier les valeurs numériques sous-jacentes en effectuant un cast sur le type sous-jacent, comme le montre l’exemple suivant.  
  
```csharp  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 Voici les avantages qu’offre l’utilisation d’un enum par rapport à un type numérique :  
  
-   Vous spécifiez clairement pour le code client les valeurs qui sont valides pour la variable.  
  
-   Dans [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)], IntelliSense répertorie les valeurs définies.  
  
 Quand vous ne spécifiez pas de valeurs pour les éléments dans la liste d’énumérateurs, les valeurs sont automatiquement incrémentées de 1. Dans l’exemple précédent, `Days.Sunday` a la valeur 0, `Days.Monday` a la valeur 1 et ainsi de suite. Quand vous créez un objet `Days`, il a la valeur par défaut `Days.Sunday` (0) si vous ne lui assignez pas une valeur explicitement. Quand vous créez un enum, sélectionnez la valeur par défaut la plus logique et affectez-lui une valeur égale à zéro. Ainsi, tous les enums auront cette valeur par défaut si aucune valeur ne leur est assignée explicitement lors de leur création.  
  
 Si la variable `meetingDay` est de type `Days`, alors (sans un cast explicite) vous pouvez uniquement lui affecter l’une des valeurs définies par `Days`. Si le jour de la réunion change, vous pouvez affecter une nouvelle valeur de `Days` à `meetingDay` :  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  Il est possible d’assigner une valeur entière arbitraire à `meetingDay`. Par exemple, cette ligne de code ne produit pas d’erreur : `meetingDay = (Days) 42`. Toutefois, vous ne devez pas le faire car l’attente implicite est qu’une variable enum ne contiendra que l’une des valeurs définies par l’enum. Affecter une valeur arbitraire à une variable de type énumération présente un risque élevé d’erreurs.  
  
 Vous pouvez affecter n’importe quelle valeur aux éléments dans la liste d’énumérateurs d’un type énumération, et vous pouvez également utiliser des valeurs calculées :  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## <a name="enumeration-types-as-bit-flags"></a>Types énumération comme indicateurs binaires  
 Vous pouvez utiliser un type énumération pour définir des indicateurs binaires, ce qui permet à une instance du type énumération de stocker n’importe quelle combinaison des valeurs définies dans la liste d’énumérateurs. (Bien entendu, certaines combinaisons peuvent ne pas être significatives ou autorisées dans votre code de programme.)  
  
 Pour créer un enum d’indicateurs binaires, vous devez appliquer l’attribut <xref:System.FlagsAttribute?displayProperty=fullName> et définir les valeurs de manière appropriée afin que les opérations au niveau du bit `AND`, `OR`, `NOT` et `XOR` puissent être effectuées sur elles. Dans l’enum d’indicateurs binaires, incluez une constante nommée avec une valeur zéro qui signifie « aucun indicateur n’est défini. » N’attribuez pas la valeur zéro à un indicateur si cela ne signifie pas « aucun indicateur n’est défini ».  
  
 Dans l’exemple suivant, une autre version de l’enum `Days`, nommée `Days2`, est définie. `Days2` a l’attribut `Flags`, et à chaque valeur est affectée la puissance de deux supérieure suivante. Cela vous permet de créer une variable `Days2` dont la valeur est `Days2.Tuesday` et `Days2.Thursday`.  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 Pour définir un indicateur sur un enum, utilisez l’opérateur binaire `OR` comme indiqué dans l’exemple suivant :  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 Pour déterminer si un indicateur spécifique est défini, utilisez une opération `AND` au niveau du bit, comme indiqué dans l’exemple suivant :  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 Pour plus d’informations sur les éléments à prendre en compte quand vous définissez des types énumération avec l’attribut <xref:System.FlagsAttribute?displayProperty=fullName>, consultez <xref:System.Enum?displayProperty=fullName>.  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Utilisation des méthodes System.Enum pour découvrir et manipuler des valeurs enum  
 Tous les enums sont des instances du type <xref:System.Enum?displayProperty=fullName>. Vous ne pouvez pas dériver de nouvelles classes à partir de <xref:System.Enum?displayProperty=fullName>, mais vous pouvez utiliser ses méthodes pour découvrir des informations et manipuler les valeurs d’une instance enum.  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 Pour plus d’informations, consultez <xref:System.Enum?displayProperty=fullName>.  
  
 Vous pouvez également créer une méthode pour un enum à l’aide d’une méthode d’extension. Pour plus d’informations, consultez [Guide pratique pour créer une méthode pour une énumération](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).  
  
## <a name="featured-book-chapter"></a>Chapitre proposé  
 [En savoir plus sur les variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Bien démarrer avec Visual C# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Enum?displayProperty=fullName>   
 [Guide de programmation C#](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)
