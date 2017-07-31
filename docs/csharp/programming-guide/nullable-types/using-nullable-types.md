---
title: Utilisation de types Nullable (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
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
ms.openlocfilehash: 0721d9f60abc4e158135d6b050953b3e63ab8cb5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-nullable-types-c-programming-guide"></a>Utilisation de types Nullable (Guide de programmation C#)
Les types Nullable peuvent représenter toutes les valeurs d’un type sous-jacent ainsi qu’une autre valeur [null](../../../csharp/language-reference/keywords/null.md). Les types Nullable sont déclarés de l’une des deux façons suivantes :  
  
 `System.Nullable<T> variable`  
  
 ou  
  
 `T? variable`  
  
 `T` est le type sous-jacent du type Nullable. `T` peut être n’importe quel type valeur, notamment `struct` ; il ne peut pas être un type référence.  
  
 Voici un exemple d’utilisation de type Nullable. Prenons une variable booléenne ordinaire. Elle peut avoir deux valeurs : true et false. Il n’existe aucune valeur qui signifie « indéfini ». Dans de nombreuses applications de programmation, notamment dans les interactions de base de données, les variables peuvent se produire dans un état indéfini. Par exemple, un champ dans une base de données peut contenir les valeurs true ou false, mais peut aussi ne contenir aucune valeur. De même, les types référence peuvent être définis sur `null` pour indiquer qu’ils ne sont pas initialisés.  
  
 Cette disparité peut surcharger le travail de programmation, avec des variables supplémentaires pour stocker les informations d’état, l’utilisation de valeurs spéciales et ainsi de suite. Le modificateur de type Nullable permet à C# de créer des variables de type valeur qui indiquent une valeur indéfinie.  
  
## <a name="examples-of-nullable-types"></a>Exemples de types Nullable  
 Tout type valeur peut être utilisé comme base d’un type Nullable. Par exemple :  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Membres de types Nullable  
 Chaque instance d’un type Nullable a deux propriétés publiques en lecture seule :  
  
-   `HasValue`  
  
     `HasValue` est de type `bool`. Elle est définie sur `true` quand la variable contient une valeur non-null.  
  
-   `Value`  
  
     `Value` est du même type que le type sous-jacent. Si `HasValue` est `true`, `Value` contient une valeur significative. Si `HasValue` est `false`, l’accès à `Value` lève une <xref:System.InvalidOperationException>.  
  
 Dans cet exemple, le membre `HasValue` est utilisé pour tester si la variable contient une valeur avant d’essayer de l’afficher.  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 Vous pouvez aussi tester une valeur comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>Conversions explicites  
 Un type Nullable peut être casté en type normal explicitement par un cast ou à l’aide de la propriété `Value`. Par exemple :  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Si une conversion définie par l’utilisateur est définie entre deux types de données, la même conversion peut également être utilisée avec les versions Nullable de ces types de données.  
  
## <a name="implicit-conversions"></a>Conversions implicites  
 Une variable de type Nullable peut être définie sur null avec le mot clé `null`, comme indiqué dans l’exemple suivant :  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 La conversion d’un type ordinaire en type Nullable est implicite.  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>Opérateurs  
 Les opérateurs unaire et binaire prédéfinis et tous les opérateurs définis par l’utilisateur existant pour les types valeur peuvent également être utilisés par les types Nullable. Ces opérateurs produisent une valeur null si les opérandes sont null ; sinon, l’opérateur utilise la valeur contenue pour calculer le résultat. Par exemple :  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Quand vous effectuez des comparaisons avec des types Nullable, si la valeur de l’un des types Nullable est null et que l’autre ne l’est pas, toutes les comparaisons donnent la valeur `false` à l’exception de `!=` (différent). Ne partez pas du principe que parce qu’une comparaison en particulier retourne `false`, l’inverse retourne `true`. Dans l’exemple suivant, 10 n’est ni supérieur, ni inférieur, ni égal à null. Seul `num1 != num2` donne la valeur `true`.  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Une comparaison d’égalité de deux types Nullable tous deux null donne la valeur `true`.  
  
## <a name="the--operator"></a>??, Opérateur  
 L’opérateur `??` définit une valeur par défaut qui est retournée quand un type Nullable est assigné à un type non-Nullable.  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Cet opérateur peut également être utilisé avec plusieurs types Nullable. Par exemple :  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>Type bool?  
 Le type Nullable `bool?` peut contenir trois valeurs différentes : [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) et [null](../../../csharp/language-reference/keywords/null.md). Pour plus d’informations sur le cast d’une valeur bool? en bool, consultez [Guide pratique pour effectuer sans risque un cast du type bool? en bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Les types booléens Nullable sont comme le type de variable booléen utilisé dans SQL. Pour vérifier que les résultats produits par les opérateurs `&` et `|` sont cohérents avec le type booléen à trois valeurs dans SQL, les opérateurs prédéfinis suivants sont fournis :  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Boxing des types Nullable](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Types valeur Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

