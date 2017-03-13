---
title: "Contraintes sur les param&#232;tres de type (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "génériques (C#), contraintes de type"
  - "contraintes de type (C#)"
  - "paramètres de type (C#), contraintes"
  - "paramètre de type indépendant (C#)"
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 41
---
# Contraintes sur les param&#232;tres de type (Guide de programmation C#)
Lorsque vous définissez une classe générique, vous pouvez appliquer des restrictions aux genres de types que le code client peut utiliser pour les arguments de type lorsqu'il instancie votre classe.  Si le code client essaie d'instancier votre classe à l'aide d'un type qui n'est pas autorisé par une contrainte, il en résultera une erreur de compilation.  Ces restrictions sont appelées des contraintes.  Les contraintes sont spécifiées à l'aide du mot clé contextuel `where`.  Le tableau suivant répertorie les six types de contraintes :  
  
|Contrainte|Description|  
|----------------|-----------------|  
|where T : struct|L'argument de type doit être un type valeur.  Tout type valeur, excepté <xref:System.Nullable>, peut être spécifié.  Consultez [Utilisation de types Nullable](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) pour plus d'informations.|  
|où T : classe|L'argument de type doit être un type référence ; cela concerne également les types de classe, d'interface ou de tableau et les types délégués.|  
|où T : new\(\)|L'argument de type doit avoir un constructeur sans paramètre public.  Lorsque vous utilisez la contrainte `new()` avec d'autres contraintes, elle doit être spécifiée en dernier :|  
|où T : \<nom de classe de base\>|L'argument de type doit être ou dériver de la classe de base spécifiée.|  
|où T : \<nom d'interface\>|L'argument de type doit être ou implémenter l'interface spécifiée.  Plusieurs contraintes d'interface peuvent être spécifiées.  L'interface qui impose les contraintes peut également être générique.|  
|où T : U|L'argument de type fourni pour T doit être ou dériver de l'argument fourni pour U.|  
  
## Pourquoi utiliser des contraintes ?  
 Si vous souhaitez examiner un élément dans une liste générique afin de déterminer s'il est valide ou pour le comparer à un autre élément, le compilateur doit être assuré que l'opérateur ou la méthode qu'il doit appeler sera prise en charge par tous les arguments de type pouvant être spécifiés par le code client.  Cette assurance est obtenue par l'application d'une ou plusieurs contraintes à votre définition de classe générique.  Par exemple, la contrainte de classe de base indique au compilateur qui seuls les objets de ce type ou dérivés de ce type seront utilisés comme arguments de type.  Lorsque le compilateur a cette assurance, il peut autoriser aux méthodes de ce type d'être appelées dans la classe générique.  Les contraintes sont appliquées à l'aide du mot clé contextuel `where`.  L'exemple de code suivant montre la fonctionnalité que nous pouvons ajouter à la classe `GenericList<T>` \(dans [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)\) en appliquant une contrainte de classe de base.  
  
 [!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 La contrainte permet à la classe générique d'utiliser la propriété `Employee.Name`, car il est garanti que tous les éléments de type T sont soit un objet `Employee`, soit un objet qui hérite de `Employee`.  
  
 Plusieurs contraintes peuvent être appliquées au même paramètre de type, et les contraintes elles\-mêmes peuvent être des types génériques, comme suit :  
  
 [!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 En contraignant le paramètre de type, vous augmentez le nombre d'opérations et d'appels de méthode autorisés au niveau de celui pris en charge par le type contraignant et tous les types dans sa hiérarchie d'héritage.  Par conséquent, en concevant des classes ou des méthodes génériques, si vous exécutez des opérations sur les membres génériques au\-delà de la simple assignation ou que vous appelez des méthodes non prises en charge par `System.Object`, vous devez appliquer des contraintes au paramètre de type.  
  
 En appliquant la contrainte `where T : class`, évitez d'utiliser les opérateurs `==` et `!=` sur le paramètre de type, car ces opérateurs testent uniquement l'identité des références, pas l'égalité des valeurs.  C'est le cas même si ces opérateurs sont surchargés dans un type utilisé comme un argument.  Le code suivant illustre ce point; la sortie a la valeur false même si la classe <xref:System.String> surcharge l'opérateur `==`.  
  
 [!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 La raison à ce comportement réside dans le fait qu'au moment de la compilation, le compilateur sait uniquement que T est un type référence, et par conséquent doit utiliser les opérateurs par défaut, valides pour tous les types référence.  Si vous devez tester l'égalité des valeurs, il est recommandé d'appliquer également la contrainte `where T : IComparable<T>` et d'implémenter cette interface dans toute classe qui sera utilisée pour construire la classe générique.  
  
## Utilisation de contraintes dans plusieurs paramètres  
 Vous pouvez appliquer des contraintes à plusieurs paramètres et plusieurs contraintes à un paramètre unique comme le montre l'exemple suivant :  
  
 [!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## Paramètres de type unbounded  
 Les paramètres de type qui n'ont aucune contrainte, tels que T dans la classe publique `SampleClass<T>{}`, sont appelés paramètres de type unbounded.  Les paramètres de type unbounded obéissent aux règles suivantes :  
  
-   Les opérateurs `!=` et `==` ne peuvent pas être utilisés parce qu'il n'y a aucune garantie que l'argument de type concret prendra en charge ces opérateurs.  
  
-   Ils peuvent être convertis vers et depuis `System.Object` ou être explicitement convertis vers tout type d'interface.  
  
-   Vous pouvez comparer à [null](../../../csharp/language-reference/keywords/null.md).  Si un paramètre unbounded est comparé à `null`, la comparaison retournera toujours la valeur false si l'argument de type est un type valeur.  
  
## Paramètres de type en tant que contraintes  
 L'utilisation d'un paramètre de type générique comme contrainte est utile lorsqu'une fonction membre dotée de son propre paramètre de type doit contraindre ce paramètre au paramètre du type conteneur, comme le montre l'exemple suivant :  
  
 [!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 Dans l'exemple précédent, `T` est une contrainte de type naked dans le contexte de la méthode `Add`, et un paramètre de type unbounded dans le contexte de la classe `List`.  
  
 Les paramètres de type peuvent également être utilisés comme contraintes dans les définitions de classes génériques.  Notez que le paramètre de type doit être déclaré dans des crochets pointus, ainsi que tous les autres paramètres de type :  
  
 [!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 L'utilité de contraintes de paramètres type avec les classes génériques est très limitée, car le compilateur ne peut rien deviner à propos du paramètre de type en dehors du fait qu'elle dérive de `System.Object`.  Utilisez des paramètres de type naked sur les classes génériques dans les scénarios dans lesquels vous souhaitez mettre en application une relation d'héritage entre deux paramètres de type.  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md)   
 [new, contrainte](../../../csharp/language-reference/keywords/new-constraint.md)