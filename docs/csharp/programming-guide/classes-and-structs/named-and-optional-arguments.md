---
title: "Arguments nommés et facultatifs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
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
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: a7f05e3e0b19bf6457989f8db2b46741cf6b28c1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Arguments nommés et facultatifs (Guide de programmation C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] introduit des arguments nommés et facultatifs. Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre particulier en associant l’argument avec le nom du paramètre plutôt qu’avec la position du paramètre dans la liste de paramètres. Les *arguments facultatifs* vous permettent d’omettre des arguments pour certains paramètres. Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.  
  
 Quand vous utilisez des arguments nommés et facultatifs, ils sont évalués selon leur ordre d’affichage dans la liste d’arguments, et non dans la liste de paramètres.  
  
 La combinaison de paramètres nommés et facultatifs vous permet de fournir des arguments uniquement pour certains paramètres d’une liste de paramètres facultatifs. Cette fonctionnalité facilite considérablement les appels aux interfaces COM telles que les API Microsoft Office Automation.  
  
## <a name="named-arguments"></a>Arguments nommés  
 Avec les arguments nommés, vous n’avez plus à mémoriser ou à rechercher l’ordre des paramètres dans les listes de paramètres des méthodes appelées. Vous pouvez spécifier le paramètre de chaque argument par son nom. Par exemple, vous pouvez appeler une fonction qui calcule l’indice de masse corporelle (IMC) à l’aide de la méthode standard consistant à envoyer les arguments du poids et de la taille par position, dans l’ordre défini par la fonction.  
  
 `CalculateBMI(123, 64);`  
  
 Si vous ne vous souvenez pas de l’ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans l’ordre que vous voulez (le poids ou la taille en premier).  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente.  
  
 Un argument nommé peut suivre des arguments de position, comme illustré ici.  
  
 `CalculateBMI(123, height: 64);`  
  
 À l’inverse, un argument de position ne peut pas suivre un argument nommé. Par exemple, l’instruction suivante provoque une erreur du compilateur.  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a>Exemple  
 Le code suivant implémente les exemples de cette section.  
  
 [!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>Arguments facultatifs  
 La définition d’une méthode, d’un constructeur, d’un indexeur ou d’un délégué peut spécifier que ses paramètres sont obligatoires ou facultatifs. Chaque appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres facultatifs.  
  
 Dans sa définition, chaque paramètre facultatif a une valeur par défaut. Si aucun argument n’est envoyé pour ce paramètre, la valeur par défaut est utilisée. Une valeur par défaut doit être l’un des types d’expressions suivants :  
  
-   une expression constante ;  
  
-   une expression de la forme `new ValType()`, où `ValType` est un type valeur (par exemple, [enum](../../../csharp/language-reference/keywords/enum.md) ou [struct](../../../csharp/programming-guide/classes-and-structs/structs.md)) ;  
  
-   une expression de la forme [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), où `ValType` est un type valeur.  
  
 Les paramètres facultatifs sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires. Si l’appelant fournit un argument pour l’un des paramètres d’une série de paramètres facultatifs, il doit fournir des arguments pour tous les paramètres facultatifs précédents. Les intervalles séparés par des virgules ne sont pas autorisés dans la liste d’arguments. Par exemple, dans le code suivant, la méthode d’instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres facultatifs.  
  
 [!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 L’appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre, mais pas pour le deuxième.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense indique les paramètres facultatifs par des crochets, comme illustré dans l’exemple suivant.  
  
 ![Info express IntelliSense pour la méthode ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
Paramètres facultatifs dans ExampleMethod  
  
> [!NOTE]
>  Vous pouvez aussi déclarer des paramètres facultatifs à l’aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET. Les paramètres `OptionalAttribute` ne nécessitent pas de valeur par défaut.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le constructeur associé à `ExampleClass` a un seul paramètre, qui est facultatif. La méthode d’instance `ExampleMethod` a un paramètre obligatoire (`required`) et deux paramètres facultatifs (`optionalstr` et `optionalint`). Le code dans `Main` montre les différentes façons dont le constructeur et la méthode peuvent être appelés.  
  
 [!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>Interfaces COM  
 Avec la prise en charge des objets dynamiques et d’autres améliorations, les arguments nommés et facultatifs améliorent nettement l’interopérabilité avec les API COM, telles que les API Office Automation.  
  
 Par exemple, la méthode [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) dans l’interface [Range](http://go.microsoft.com/fwlink/?LinkId=148196) de Microsoft Office Excel comporte sept paramètres, qui sont tous facultatifs. Ces paramètres sont indiqués dans l’illustration suivante.  
  
 ![Info express IntelliSense pour la méthode AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Paramètres AutoFormat  
  
 Dans C# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l’exemple suivant.  
  
 [!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 Toutefois, vous pouvez considérablement simplifier l’appel à `AutoFormat` en utilisant les arguments nommés et facultatifs introduits dans C# 4.0. Les paramètres nommés et facultatifs vous permettent d’omettre l’argument d’un paramètre obligatoire si vous ne souhaitez pas modifier la valeur par défaut du paramètre. Dans l’appel suivant, une valeur est spécifiée pour un seul des sept paramètres.  
  
 [!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Pour plus d’informations et obtenir des exemples, consultez [Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) et [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Résolution de surcharge  
 L’utilisation d’arguments nommés et facultatifs affecte la résolution de surcharge des manières suivantes :  
  
-   Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par son nom ou sa position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.  
  
-   Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés. Les arguments omis pour les paramètres facultatifs sont ignorés.  
  
-   Si deux candidats sont jugés de qualité équivalente, la préférence va à celui qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel. Ceci s’explique par l’application d’une préférence générale dans la résolution de surcharge en faveur des candidats qui ont le moins de paramètres.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Utilisation d’indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)

