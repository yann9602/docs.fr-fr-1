---
title: "Utilisation de types Nullable (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "types Nullable (C#), à propos des types Nullable"
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# Utilisation de types Nullable (Guide de programmation C#)
Les types Nullable peuvent représenter toutes les valeurs d'un type sous\-jacent, et une valeur [Null](../../../csharp/language-reference/keywords/null.md) supplémentaire.  Les types Nullable peuvent se déclarer de deux manières :  
  
 `System.Nullable<T> variable`  
  
 ou  
  
 `T?  variable`  
  
 `T` est le type sous\-jacent du type Nullable.  `T` peut correspondre à tout type de valeur notamment `struct`; il ne peut pas s'agir d'un type de référence.  
  
 Pour obtenir un exemple de situation où vous pouvez utiliser un type Nullable, voyez comment une variable booléenne ordinaire peut avoir deux valeurs : true et false.  Il n'existe aucune valeur qui signifie « indéfini ».  Dans de nombreuses applications de programmation, notamment dans les interactions de bases de données, des variables peuvent avoir un état indéfini.  Par exemple, un champ dans une base de données peut contenir les valeurs true ou false, mais il peut aussi ne contenir aucune valeur du tout.  De la même façon, les types référence peuvent avoir la valeur `null` pour indiquer qu'ils ne sont pas initialisés.  
  
 Cette disparité peut créer un travail de programmation supplémentaire, avec des variables supplémentaires utilisées pour stocker des informations d'état, l'utilisation de valeurs spéciales, et ainsi de suite.  Le modificateur de type Nullable permet à C\# de créer des variables de type valeur pouvant contenir une valeur indéfinie.  
  
## Exemples de types Nullable  
 N'importe quel type valeur peut être utilisé comme base de type Nullable.  Par exemple :  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## Membres des types Nullable  
 Chaque instance de type Nullable a deux propriétés publiques en lecture seule :  
  
-   `HasValue`  
  
     `HasValue` est de type `bool`.  Elle a la valeur `true` lorsque la variable contient une valeur non Null.  
  
-   `Value`  
  
     `Value` est du même type que le type sous\-jacent.  Si `HasValue` a la valeur `true`, `Value` contient une valeur significative.  Si `HasValue` est `false`, l'accès à `Value` lève une exception <xref:System.InvalidOperationException>.  
  
 Dans cet exemple, le membre `HasValue` est utilisé pour tester si la variable contient une valeur avant d'essayer de l'afficher.  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 Vous pouvez également vérifier une valeur de la manière suivante :  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## Conversions explicites  
 Un type Nullable peut être converti \(cast\) en un type normal, soit explicitement par un cast, soit à l'aide de la propriété `Value`.  Par exemple :  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Si une conversion définie par l'utilisateur est définie entre deux types de données, la même conversion peut également être utilisée avec les versions Nullable de ces types de données.  
  
## Conversions implicites  
 Il est possible d'affecter à une variable de type Nullable la valeur Null avec le mot clé `null`, comme illustré ci\-dessous :  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 La conversion d'un type ordinaire en un type Nullable, est implicite.  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## Opérateurs  
 Les opérateurs unaires et binaires prédéfinis, et tout opérateur défini par l'utilisateur, qui existent pour les types valeur peuvent également être utilisés par les types Nullable.  Ces opérateurs produisent une valeur Null si les opérandes sont Null. Sinon, l'opérateur utilise la valeur contenue pour calculer le résultat.  Par exemple :  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Lorsque vous effectuez des comparaisons avec les types Nullable, si la valeur de l'un des types Nullable est Null et que l'autre ne l'est pas, toutes les comparaisons prennent la valeur `false` à l'exception de `!=` \(différent\).  Ne pensez pas que si une comparaison particulière retourne `false`, le cas contraire retourne `true`.  Dans l'exemple suivant, 10 n'est ni supérieur à, ni inférieur à, ni égal à Null.  Seul `num1 != num2` prend la valeur `true`.  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Une comparaison d'égalité de deux types Nullable qui sont Null prend la valeur `true`.  
  
## OpérateurOpérateur  
 L'opérateur `??` définit une valeur par défaut qui est retournée lorsqu'un type Nullable est assigné à un type non Nullable.  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Cet opérateur peut également être utilisé avec plusieurs types Nullable.  Par exemple :  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## Typetype  
 Le type Nullable `bool?` peut contenir trois valeurs différentes : [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) et [Null](../../../csharp/language-reference/keywords/null.md).  Pour plus d'informations sur la façon d'effectuer une conversion de type \(transtypage\) à partir d'un bool ?  vers un bool, consultez [Comment : effectuer sans risque un cast du type bool? en bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Les types booléens Nullable sont semblables au type de variable booléenne utilisé en SQL.  Pour garantir que les résultats produits par le `&` et  `|` les opérateurs sont cohérents avec le type booléen de valeur trois dans SQL, les opérateurs prédéfinis suivants sont fournis :  
  
 `bool?  operator &(bool?  x, bool?  y)`  
  
 `bool?  operator |(bool?  x, bool?  y)`  
  
 Les résultats de ces opérateurs sont répertoriés dans le tableau suivant :  
  
|X|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Boxing des types Nullable](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)