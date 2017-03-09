---
title: "Champs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "champs (C#)"
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# Champs (Guide de programmation C#)
Un *champ* est une variable de tout type déclaré directement dans une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md).  Les champs sont des *membres* de leur type contenant.  
  
 Une classe ou un struct peut avoir des champs d'instance ou des champs statiques, ou les deux.  Les champs d'instance sont spécifiques à une instance d'un type.  Si vous avez une classe T avec un champ d'instance F, vous pouvez créer deux objets de type T et modifier la valeur de F dans chaque objet sans affecter la valeur dans l'autre objet.  Par contraste, un champ statique appartient à la classe elle\-même et est partagé par toutes les instances de cette classe.  Les modifications effectuées à partir de l'instance A seront visibles immédiatement aux instances B et C si elles accèdent au champ.  
  
 En général, vous devez utiliser des champs uniquement pour des variables qui ont une accessibilité privée ou protégée.  Les données que votre classe expose au code client doivent être fournies par le biais de [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) et [indexeurs](../../../csharp/programming-guide/indexers/index.md).  En utilisant ces constructions pour l'accès indirect aux champs internes, vous pouvez vous protéger contre les valeurs d'entrée non valides.  Un champ privé qui stocke les données exposées par une propriété publique porte le nom de *magasin de stockage* ou *champ de stockage*.  
  
 Les champs stockent en général les données qui doivent être accessibles à plusieurs méthodes de classe et qui doivent être stockées davantage que la durée de vie d'une méthode unique.  Par exemple, une classe qui représente une date de calendrier peut avoir trois champs à nombre entier : un pour le mois, un pour le jour et un pour l'année.  Les variables qui ne sont pas utilisées hors de la portée d'une méthode unique doivent être déclarées comme *variables locales* dans le corps de méthode lui\-même.  
  
 Les champs sont déclarés dans le bloc de classe en spécifiant le niveau d'accès du champ, suivi du type du champ, suivi du nom du champ.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_1.cs)]  
  
 L'accès à un champ dans un objet se fait en ajoutant un point après le nom d'objet, suivi du nom du champ, comme dans `objectname.fieldname`.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_2.cs)]  
  
 Un champ peut se voir affecter une valeur initiale à l'aide de l'opérateur d'assignation dans la déclaration de champ.  Par exemple, pour donner automatiquement au champ `day` la valeur `"Monday"`, déclarez `day` comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_3.cs)]  
  
 Les champs sont initialisés immédiatement avant le constructeur pour l'instance d'objet appelée.  Si le constructeur assigne la valeur d'un champ, il remplace toute valeur donnée au cours de la déclaration de champ.  Pour plus d'informations, consultez [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Un initialiseur de champ ne peut pas faire référence à d'autres champs d'instance.  
  
 Les champs peuvent être marqués comme étant [publics](../../../csharp/language-reference/keywords/public.md), [privés](../../../csharp/language-reference/keywords/private.md), [protégés](../../../csharp/language-reference/keywords/protected.md), [internes](../../../csharp/language-reference/keywords/internal.md) ou  `protected internal`.  Ces modificateurs d'accès définissent comment les utilisateurs de la classe peuvent accéder aux champs.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Un champ peut être déclaré [statique](../../../csharp/language-reference/keywords/static.md) facultativement.  Cela rend le champ disponible aux appelants à tout moment, même si aucune instance de la classe n'existe.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Un champ peut être déclaré [en lecture seule](../../../csharp/language-reference/keywords/readonly.md).  Un champ en lecture seule peut uniquement se voir assigner une valeur pendant l'initialisation ou dans un constructeur.  Un champ `static` `readonly` est très semblable à une constante, à ceci près que le compilateur C\# n'a pas accès à la valeur d'un champ statique en lecture seule au moment de la compilation, uniquement au moment de l'exécution.  Pour plus d'informations, consultez [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)