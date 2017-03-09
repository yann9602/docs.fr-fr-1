---
title: "Arguments nomm&#233;s et facultatifs (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "namedParameter_CSharpKeyword"
  - "cs_namedParameter"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arguments (C#), nommés"
  - "arguments (C#), facultatifs"
  - "arguments nommés et facultatifs (C#)"
  - "arguments nommés (C#)"
  - "arguments facultatifs (C#)"
  - "paramètres (C#), nommés"
  - "paramètres (C#), facultatifs"
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# Arguments nomm&#233;s et facultatifs (Guide de programmation&#160;C#)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)] introduit des arguments nommés et facultatifs.  Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre particulier en l'associant au nom du paramètre, et non pas à la position du paramètre dans la liste de paramètres.  Les *arguments facultatifs* vous permettent d'omettre des arguments pour certains paramètres.  Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.  
  
 Lorsque vous utilisez les arguments nommés et facultatifs, ils sont évalués selon leur ordre d'affichage dans la liste d'arguments, et non pas dans la liste de paramètres.  
  
 Lorsqu'ils sont utilisés ensemble, les paramètres nommés et optionnels vous permettent de fournir des arguments pour seulement quelques paramètres d'une liste de paramètres optionnels.  Cette fonctionnalité facilite considérablement les appels aux interfaces COM telles que les API d'automation de Microsoft Office.  
  
## Arguments nommés  
 Les arguments nommés vous évitent d'avoir à mémoriser ou à rechercher l'ordre des paramètres dans les listes de paramètres des méthodes appelées.  Le paramètre de chaque argument peut être spécifié par son nom.  Par exemple, une fonction qui calcule l'indice de masse corporelle \(IMC\) peut être appelée de la façon standard par l'envoi d'arguments pour le poids et la hauteur par position, dans l'ordre défini par la fonction.  
  
 `CalculateBMI(123, 64);`  
  
 Si vous ne vous souvenez pas de l'ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans n'importe quel ordre \(le poids ou la hauteur en premier\).  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente.  
  
 Un argument nommé peut suivre des arguments de position, comme illustré ici.  
  
 `CalculateBMI(123, height: 64);`  
  
 Toutefois, un argument de position ne peut pas suivre un argument nommé.  L'instruction suivante entraîne une erreur du compilateur.  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## Exemple  
 Le code suivant implémente les exemples de cette section.  
  
 [!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/program.cs#1)]  
  
## Arguments facultatifs  
 La définition d'une méthode, d'un constructeur, d'un indexeur ou d'un délégué peut spécifier que ses paramètres sont obligatoires ou optionnels.  Tout appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres optionnels.  
  
 Chaque paramètre optionnel est associé à une valeur par défaut dans le cadre de sa définition.  Si aucun argument n'est envoyé pour ce paramètre, la valeur par défaut est utilisée.  une valeur par défaut doit être l'un des types suivants d'expressions :  
  
-   une expression constante ;  
  
-   une expression du formulaire `new ValType()`, où `ValType` est un type valeur, tel qu' [enum](../../../csharp/language-reference/keywords/enum.md) ou [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   une expression du formulaire [valeur par défaut \(ValType\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md), où `ValType` est un type valeur.  
  
 Les paramètres optionnels sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires.  Si l'appelant fournit un argument pour l'un des paramètres d'une suite de paramètres optionnels, il doit spécifier des arguments pour tous les paramètres optionnels précédents.  Les intervalles séparés par des virgules ne sont pas pris en charge dans la liste d'arguments.  Par exemple, dans le code suivant, la méthode d'instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres optionnels.  
  
 [!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/optional.cs#15)]  
  
 L'appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre mais pas pour le deuxième.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense utilise des parenthèses pour signaler les paramètres optionnels, comme illustré ci\-après.  
  
 ![Info express IntelliSense pour la méthode ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional-parameters.png "Optional\_Parameters")  
Paramètres optionnels dans ExampleMethod  
  
> [!NOTE]
>  Vous pouvez également déclarer des paramètres optionnels à l'aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET.  Les paramètres `OptionalAttribute` ne requièrent pas de valeur par défaut.  
  
## Exemple  
 Dans l'exemple suivant, le constructeur associé à `ExampleClass` comporte un paramètre, qui est optionnel.  La méthode d'instance `ExampleMethod` comporte un paramètre obligatoire, `required`, et deux paramètres optionnels, `optionalstr` et `optionalint`.  Le code de `Main` illustre les différentes façons dont le constructeur et la méthode peuvent être appelés.  
  
 [!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/optional.cs#2)]  
  
## Interfaces COM  
 Avec la prise en charge des objets dynamiques et d'autres améliorations, les arguments nommés et facultatifs améliorent considérablement l'interopérabilité avec les API COM, telles que les API d'automation Office.  
  
 Par exemple, la méthode [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) dans l'interface Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) comporte sept paramètres qui sont tous optionnels.  Ces paramètres sont indiqués dans l'illustration suivante.  
  
 ![Info express IntelliSense pour la méthode AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat-parameters.png "AutoFormat\_Parameters")  
Paramètres AutoFormat  
  
 Dans la version C\# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/namedandoptcom.cs#3)]  
  
 Toutefois, vous pouvez simplifier considérablement l'appel à `AutoFormat` à l'aide des arguments nommés et optionnels introduits dans la version C\# 4.0.  Les arguments nommés et optionnels vous permettent d'omettre l'argument pour un paramètre optionnel si vous ne souhaitez pas modifier la valeur par défaut du paramètre.  Dans l'appel suivant, une valeur est spécifiée pour un seul des sept paramètres.  
  
 [!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/namedandoptcom.cs#13)]  
  
 Pour plus d'informations et d'exemples, consultez [Comment : utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) et [Comment : accéder aux objets Office Interop à l'aide des fonctionnalités Visual C\#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## Résolution de surcharge  
 L'utilisation des arguments nommés et facultatifs affecte la résolution de surcharge de différentes manières :  
  
-   Une méthode, un indexeur ou un constructeur est candidat pour l'exécution si d'une part, chacun de ses paramètres est optionnel ou correspond, par nom ou par position, à un argument unique de l'instruction appelante et que d'autre part, cet argument peut être converti vers le type du paramètre.  
  
-   Si plusieurs candidats existent, les règles de résolution de surcharge des conversions par défaut sont appliquées aux arguments qui sont explicitement spécifiés.  Les arguments omis pour les paramètres optionnels sont ignorés.  
  
-   Si deux candidats sont jugés aussi appropriés l'un que l'autre, la préférence va à celui qui ne comporte pas de paramètres optionnels pour lesquels les arguments ont été omis dans l'appel.  Cela s'explique par une préférence générale, dans la résolution de surcharge, en faveur des candidats comportant moins de paramètres.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Comment : utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Utilisation d'indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)