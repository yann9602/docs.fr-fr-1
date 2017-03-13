---
title: "Utilisation de propri&#233;t&#233;s (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "get (accesseur C#)"
  - "propriétés (C#), à propos des propriétés"
  - "set (accesseur C#)"
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# Utilisation de propri&#233;t&#233;s (Guide de programmation C#)
Les propriétés combinent des aspects à la fois des champs et des méthodes.  Aux yeux de l'utilisateur d'un objet, une propriété semble être un champ. L'accès à la propriété demande exactement la même syntaxe.  Pour l'implémenteur d'une classe, une propriété est constituée d'un ou de deux blocs de code, représentant un accesseur [get](../../../csharp/language-reference/keywords/get.md) et\/ou un accesseur [set](../../../csharp/language-reference/keywords/set.md).  Le bloc de code de l'accesseur `get` est exécuté à la lecture de la propriété ; le bloc de code de l'accesseur `set` est exécuté à l'assignation d'une nouvelle valeur à la propriété.  Une propriété sans accesseur `set` est considérée comme étant en lecture seule.  Une propriété sans accesseur `get` est considérée comme étant en écriture seule.  Une propriété comportant les deux accesseurs est en lecture\-écriture.  
  
 Contrairement aux champs, les propriétés ne sont pas classées en tant que variables.  Par conséquent, vous ne pouvez pas passer une propriété en tant que paramètre [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 Les propriétés ont de multiples utilisations : elles peuvent valider des données avant d'autoriser une modification ; elles peuvent exposer de façon transparente sur une classe des données récupérées de quelque autre source, telle qu'une base de données ; elles peuvent effectuer une action à la suite d'une modification de données, par exemple déclencher un événement ou modifier les valeurs d'autres champs.  
  
 Pour déclarer les propriétés dans le bloc de classe, vous devez spécifier le niveau d'accès du champ, suivi du type puis du nom de la propriété, et enfin d'un bloc de code qui déclare un accesseur `get` et\/ou un accesseur `set`.  Par exemple :  
  
 [!code-cs[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Dans cet exemple, `Month` est déclaré comme une propriété afin que l'accesseur `set` puisse s'assurer que la valeur `Month` est définie entre 1 et 12.  La propriété `Month` utilise un champ privé pour suivre la valeur réelle.  L'emplacement réel des données d'une propriété est souvent appelé « magasin de stockage » de la propriété. Il est courant pour les propriétés d'utiliser des champs privés comme magasin de stockage.  Le champ reçoit un marqueur indiquant qu'il est privé pour garantir qu'il ne pourra être modifié que par appel de la propriété.  Pour plus d'informations sur les restrictions d'accès public et privé, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Les propriétés implémentées automatiquement fournissent une syntaxe simplifiée pour les déclarations de propriété simples.  Pour plus d'informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## Accesseur get  
 Le corps de l'accesseur `get` ressemble à celui d'une méthode.  Il doit retourner une valeur de type de propriété.  L'exécution de l'accesseur `get` équivaut à la lecture de la valeur du champ.  Par exemple, lorsque vous retournez la variable privée de l'accesseur `get` et que les optimisations sont activées, le compilateur fait en sorte que l'appel à la méthode d'accesseur `get` soit inline pour qu'il n'y ait pas surcharge d'appels à la méthode.  Toutefois, une méthode d'accesseur `get` virtuelle ne peut pas être inline, car le compilateur ne sait pas au moment de la compilation quelle méthode sera réellement appelée à l'exécution.  Voici un accesseur `get` qui retourne la valeur d'un champ privé `name` :  
  
 [!code-cs[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Lorsque vous référencez la propriété, sauf dans le cas où il s'agit de la cible d'une assignation, l'accesseur `get` est appelé pour lire la valeur de la propriété.  Par exemple :  
  
 [!code-cs[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 L'accesseur `get` doit se terminer dans une instruction [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md), et le contrôle ne peut pas s'écouler du corps de l'accesseur.  
  
 Modifier l'état de l'objet à l'aide de l'accesseur `get` n'est pas une bonne habitude de programmation.  Par exemple, l'accesseur ci\-dessous a pour effet secondaire de modifier l'état de l'objet à chaque accès au champ `number`.  
  
 [!code-cs[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 L'accesseur `get` peut être utilisé pour retourner la valeur du champ ou pour la calculer et la retourner.  Par exemple :  
  
 [!code-cs[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 Dans le segment de code précédent, si vous n'assignez pas de valeur à la propriété `Name`, une valeur NA est retournée.  
  
## Accesseur set  
 L'accesseur `set` est semblable à une méthode dont le type de retour est [void](../../../csharp/language-reference/keywords/void.md).  Il utilise un paramètre implicite nommé `value`, dont le type est celui de la propriété.  Dans l'exemple suivant, un accesseur `set` est ajouté à la propriété `Name` :  
  
 [!code-cs[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Lorsque vous assignez une valeur à la propriété, l'accesseur `set` est appelé à l'aide d'un argument qui fournit la nouvelle valeur.  Par exemple :  
  
 [!code-cs[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 C'est une erreur d'utiliser le nom du paramètre implicite `value` pour une déclaration de variable locale dans un accesseur `set`.  
  
## Notes  
 Les propriétés peuvent être marquées comme `public`, `private`, `protected`, `internal` ou `protected internal`.  Ces modificateurs d'accès définissent la façon dont les utilisateurs de la classe ont accès à la propriété.  Les accesseurs `get` et `set` d'une même propriété peuvent avoir des modificateurs d'accès différents.  Par exemple, `get` peut être `public` pour autoriser l'accès en lecture seule depuis l'extérieur du type et `set` peut être `private` ou `protected`.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Une propriété peut être déclarée comme étant statique à l'aide du mot clé `static`.  Elle devient ainsi disponible aux appelants à tout moment, même s'il n'existe aucune instance de la classe.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Une propriété peut être marquée comme étant virtuelle à l'aide du mot clé [virtual](../../../csharp/language-reference/keywords/virtual.md).  Cela permet aux classes dérivées de se substituer au comportement de la propriété à l'aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).  Pour plus d'informations sur ces options, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Une propriété qui se substitue à une propriété virtuelle peut également être [sealed](../../../csharp/language-reference/keywords/sealed.md), ce qui spécifie que pour les classes dérivées elle n'est plus virtuelle.  Enfin, une propriété peut être déclarée [abstract](../../../csharp/language-reference/keywords/abstract.md).  Cela signifie qu'il n'existe aucune implémentation dans la classe et que les classes dérivées doivent écrire leur propre implémentation.  Pour plus d'informations sur ces options, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Utiliser un modificateur [virtuels](../../../csharp/language-reference/keywords/virtual.md), [abstract](../../../csharp/language-reference/keywords/abstract.md) ou [override](../../../csharp/language-reference/keywords/override.md) sur un accesseur d'une propriété [statique](../../../csharp/language-reference/keywords/static.md) est une erreur.  
  
## Exemple  
 Cet exemple illustre les propriétés d'instance, statiques et en lecture seule.  Il accepte le nom de l'employé à partir du clavier, incrémente `NumberOfEmployees` d'une unité et affiche le nom et le matricule de l'employé.  
  
 [!code-cs[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## Exemple  
 Cet exemple illustre comment accéder à une propriété dans une classe de base masquée par une autre propriété portant le même nom dans une classe dérivée.  
  
 [!code-cs[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Points importants de l'exemple précédent :  
  
-   La propriété `Name` dans la classe dérivée masque la propriété `Name` dans la classe de base.  Dans ce cas, le modificateur `new` est utilisé dans la déclaration de la propriété dans la classe dérivée :  
  
     [!code-cs[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Le cast `(Employee)` permet d'accéder à la propriété masquée dans la classe de base :  
  
     [!code-cs[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Pour plus d'informations sur le masquage de membres, consultez [new, modificateur](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## Exemple  
 Dans cet exemple, deux classes, `Cube` et `Square`, implémentent une classe abstraite, `Shape`, et substituent sa propriété abstract `Area`.  Notez l'utilisation du modificateur [override](../../../csharp/language-reference/keywords/override.md) sur les propriétés.  Le programme accepte l'arête comme entrée et calcule la surface du carré et du cube.  Il accepte aussi la surface comme entrée et calcule l'arête correspondante du carré et du cube.  
  
 [!code-cs[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Propriétés d'interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)   
 [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)