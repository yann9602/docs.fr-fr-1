---
title: "Cast et conversions de types (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "caster (C#)"
  - "conversions (C#), type"
  - "convertir des types (C#)"
  - "conversion de type de données (C#)"
  - "conversions numériques (C#)"
  - "conversion de type (C#)"
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 52
---
# Cast et conversions de types (Guide de programmation C#)
C\# est typé statiquement lors de la compilation : une fois déclarée, une variable ne peut donc plus être redéclarée ou utilisée pour stocker des valeurs d'un autre type, sauf si ce type peut être converti au type de la variable.  Par exemple, il n'y a pas de conversion possible entre un entier et une chaîne arbitraire.  Ainsi, après avoir déclaré `i` comme entier, vous ne pouvez pas lui assigner la chaîne "Hello" comme le montre le code suivant.  
  
```c#  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 Toutefois, vous avez parfois besoin de copier une valeur dans un paramètre de variable ou de méthode d'un autre type.  Par exemple, vous pouvez avoir une variable de type entier que vous devez passer à une méthode dont le paramètre est de type `double`.  Il peut également arriver que vous ayez à assigner une variable de classe à une variable de type interface.  Ces types d'opérations sont appelés *conversions de types*.  En C\#, vous pouvez effectuer les types de conversions suivants :  
  
-   **Conversions implicites** : aucune syntaxe spéciale n'est requise parce que la conversion est de type sécurisé et que les données ne seront pas perdues.  Les exemples incluent des conversions de types intégraux en d'autres, plus importants, et des conversions de classes dérivées en classes de base.  
  
-   **Conversions explicites \(casts\)** : les conversions explicites requièrent un opérateur de cast.  Le transtypage est requis lorsque les données peuvent être perdues lors de la conversion, ou lorsque la conversion peut ne pas réussir pour d'autres raisons.  Les exemples classiques comprennent la conversion numérique à un type qui a moins de précision ou une plus petite plage, et la conversion d'une instance de classe de base pour une classe dérivée.  
  
-   **Conversions définies par l'utilisateur** : les conversions définies par l'utilisateur sont effectuées par des méthodes spéciales que vous pouvez définir pour permettre des conversions explicites ou implicites entre des types personnalisés qui n'ont pas de relation classe de base\/classe dérivée.  Pour plus d'informations, consultez [Conversion, opérateurs](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Conversions avec les classes d'assistance** : pour effectuer une conversion entre des types non compatibles, tels que des entiers et des objets <xref:System.DateTime?displayProperty=fullName> ou des chaînes hexadécimales et des tableaux d'octets, vous pouvez utiliser la classe <xref:System.BitConverter?displayProperty=fullName>, la classe <xref:System.Convert?displayProperty=fullName> et les méthodes `Parse` des types numériques intégrés, comme <xref:System.Int32.Parse%2A?displayProperty=fullName>.  Pour plus d'informations, consultez [Comment : convertir un tableau de byte en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Comment : convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) et [Comment : effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## Conversions implicites  
 Pour les types numériques intégrés, une conversion implicite peut être effectuée lorsque la valeur à stocker peut tenir dans la variable sans être tronquée ni arrondie.  Par exemple, une variable de type [long](../../../csharp/language-reference/keywords/long.md) \(entier sur 8 octets\) peut stocker toute valeur qu'[int](../../../csharp/language-reference/keywords/int.md) \(4 octets sur un ordinateur 32 bits\) peut stocker.  Dans l'exemple suivant, le compilateur convertit implicitement la valeur à droite en un type `long` avant de l'assigner à `bigNum`.  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/casting-and-type-convers_1.cs)]  
  
 Pour une liste complète de toutes les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Pour les types référence, il existe toujours une conversion implicite entre une classe et l'une de ses interfaces ou classes de base directes ou indirectes.  Aucune syntaxe spéciale n'est nécessaire parce qu'une classe dérivée contient toujours tous les membres d'une classe de base.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## Conversions explicites  
 Toutefois, si une conversion ne peut pas être faite sans risque de perte d'informations, le compilateur requiert que vous effectuiez une conversion explicite, appelée *cast*.  Un cast est une façon d'informer explicitement le compilateur que vous projetez de faire la conversion et que vous êtes informé qu'une perte de données peut se produire.  Pour effectuer un cast, spécifiez le type voulu entre parenthèses devant la valeur ou la variable à convertir.  Le programme suivant effectue un cast d'un caractère [double](../../../csharp/language-reference/keywords/double.md) en un caractère [int](../../../csharp/language-reference/keywords/int.md).  Le programme ne se compile pas sans le cast.  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/casting-and-type-convers_2.cs)]  
  
 Pour une liste des conversions numériques explicites autorisées, consultez [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Pour les types référence, un cast explicite est requis si vous devez effectuer une conversion d'un type de base à un type dérivé :  
  
```c#  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Une opération cast entre types référence ne modifie pas le type au moment de l'exécution de l'objet sous\-jacent ; il modifie seulement le type de la valeur utilisée comme référence à cet objet.  Pour plus d'informations, consultez [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## Exceptions de conversion de type au moment de l'exécution  
 Dans certaines conversions de types référence, le compilateur ne peut pas déterminer si un cast sera valide.  Il est possible qu'une opération cast dont la compilation fonctionne échoue au moment de l'exécution.  Comme l'illustre l'exemple suivant, un cast de type qui échoue au moment de l'exécution provoquera la levée d'une <xref:System.InvalidCastException>.  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/casting-and-type-convers_3.cs)]  
  
 C\# fournit les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md) pour vous permettre de tester la compatibilité avant d'effectuer réellement un cast.  Pour plus d'informations, consultez [Comment : effectuer sans risque un cast à l'aide des opérateurs as et is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Chapitre proposé  
 [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [\(\), opérateur](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicites](../../../csharp/language-reference/keywords/explicit.md)   
 [implicites](../../../csharp/language-reference/keywords/implicit.md)   
 [Conversion, opérateurs](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [Generalized Type Conversion](../Topic/Generalized%20Type%20Conversion.md)   
 [Exported Type Conversion](http://msdn.microsoft.com/fr-fr/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [Comment : convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)