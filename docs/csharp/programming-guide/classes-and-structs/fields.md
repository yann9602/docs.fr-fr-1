---
title: Champs (guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1e5b1880e6821b2fd4595baad31f7a1bd5599ac4
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="fields-c-programming-guide"></a>Champs (Guide de programmation C#)
Un *champ* est une variable de tout type qui est déclarée directement dans une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md). Les champs sont *membres* de leur type contenant.  
  
 Les classes et les structs peuvent avoir des champs d’instance ou des champs statiques, ou les deux. Les champs d’instance sont spécifiques à une instance de type. Si vous avez une classe T avec un champ d’instance F, vous pouvez créer deux objets de type T et modifier la valeur de F dans chaque objet, sans affecter la valeur de l’autre objet. En revanche, un champ statique appartient à la classe, et il est partagé entre toutes les instances de cette classe. Les modifications apportées à l’instance A seront visibles immédiatement aux instances B et C si elles accèdent au champ.  
  
 En règle générale, vous devez utiliser des champs uniquement pour les variables dont l’accessibilité est privée ou protégée. Les données que votre classe expose au code client doivent être fournies via des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) et des [indexeurs](../../../csharp/programming-guide/indexers/index.md). L’utilisation de ces constructions pour l’accès indirect aux champs internes permet d’éviter les valeurs d’entrée non valides. Un champ privé qui stocke les données exposées par une propriété publique est appelé *magasin de stockage* ou *champ de stockage*.  
  
 En général, les champs stockent les données qui doivent être accessibles à plusieurs méthodes de classe et doivent être stockées plus longtemps que la durée de vie d’une méthode. Par exemple, une classe qui représente une date de calendrier peut avoir trois champs de type entier : un pour le mois, un pour le jour et un pour l’année. Les variables qui ne sont pas utilisées en dehors de la portée d’une méthode doivent être déclarées comme des *variables locales* dans le corps de la méthode.  
  
 Les champs sont déclarés dans le bloc Class en spécifiant le niveau d’accès du champ, suivi du type du champ, puis du nom du champ. Exemple :  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Pour accéder à un champ dans un objet, ajoutez un point après le nom de l’objet, suivi du nom du champ, comme dans `objectname.fieldname`. Exemple :  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Une valeur initiale peut être attribuée à un champ à l’aide de l’opérateur d’assignation, lorsque le champ est déclaré. Pour assigner automatiquement le champ `day` à `"Monday"`, par exemple, vous devez déclarer `day`, comme dans l’exemple suivant :  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Les champs sont initialisés juste avant le constructeur pour l’instance d’objet qui est appelée. Si le constructeur assigne la valeur d’un champ, la valeur assignée pendant la déclaration du champ sera remplacée. Pour plus d’informations, consultez [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Un initialiseur de champ ne peut pas référencer d’autres champs d’instance.  
  
 Les champs peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`. Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder aux champs. Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Facultatif : vous pouvez déclarer un champ comme [static](../../../csharp/language-reference/keywords/static.md). Ainsi, le champ est disponible à tout moment pour les appelants, même si aucune instance de la classe n’existe. Pour plus d’informations, consultez [Classes static et membres de classe static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Un champ peut être déclaré comme [readonly](../../../csharp/language-reference/keywords/readonly.md). Un champ en lecture seule ne peut recevoir de valeur que pendant l’initialisation ou dans un constructeur. Un champ `static``readonly` est très similaire à une constante, à ceci près que le compilateur C# n’a pas accès à la valeur d’un champ statique en lecture seule au moment de la compilation, mais seulement au moment de l’exécution. Pour plus d’informations, consultez [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
