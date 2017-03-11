---
title: "Classes statiques et membres de classe statique (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, classes statiques"
  - "langage C#, membres statiques"
  - "membres de classes statiques (C#)"
  - "classes statiques (C#)"
  - "membres statiques (C#)"
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: 49
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 49
---
# Classes statiques et membres de classe statique (Guide de programmation C#)
Une classe [statique](../../../csharp/language-reference/keywords/static.md) est fondamentalement identique à une classe non statique, à une différence près : une classe statique ne peut pas être instanciée.  En d'autres termes, vous ne pouvez pas utiliser le mot clé [new](../../../csharp/language-reference/keywords/new.md) pour créer une variable du type classe.  Étant donné qu'il n'y a aucune variable d'instance, vous accédez aux membres d'une classe statique en utilisant le nom de classe lui\-même.  Par exemple, si vous avez une classe statique nommée `UtilityClass` qui a une méthode publique nommée `MethodA`, vous appelez la méthode comme illustré dans l'exemple suivant :  
  
```c#  
UtilityClass.MethodA();  
```  
  
 Une classe statique peut être utilisée comme conteneur commode pour les ensembles de méthodes qui opèrent simplement sur des paramètres d'entrée et n'ont pas à obtenir ou définir de champs d'instance internes.  Par exemple, dans la Bibliothèque de classes .NET Framework, la classe <xref:System.Math?displayProperty=fullName> statique contient plusieurs méthodes qui exécutent des opérations mathématiques, sans qu'il soit nécessaire de stocker ou extraire des données uniques à une instance particulière de la classe <xref:System.Math>.  Autrement dit, vous implémentez les membres de la classe en spécifiant le nom de la classe et le nom de la méthode, comme indiqué dans l'exemple suivant.  
  
```  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
  
```  
  
 Comme c'est le cas avec tous les types classe, les informations de type pour une classe statique sont chargées par le Common Language Runtime \(CLR\) [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] lorsque le programme qui fait référence à la classe est chargé. Le programme ne peut pas spécifier exactement quand la classe est chargée.  Toutefois, il est assuré d'être chargé et d'avoir ses champs initialisés et son constructeur statique appelé avant que la classe soit référencée pour la première fois dans votre programme.  Un constructeur statique est appelé une seule fois et une classe statique reste en mémoire pendant la durée de vie du domaine d'application dans lequel votre programme réside.  
  
> [!NOTE]
>  Pour créer une classe non statique qui autorise la création d'une seule instance d'elle\-même, consultez [Implementing Singleton in C\#](http://go.microsoft.com/fwlink/?LinkID=100567).  
  
 La liste suivante fournit les caractéristiques principales d'une classe statique :  
  
-   Contient uniquement des membres statiques.  
  
-   Ne peut pas être instanciée.  
  
-   Est sealed.  
  
-   Ne peut pas contenir de [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 La création d'une classe statique est par conséquent très semblable à la création d'une classe qui contient uniquement des membres statiques et un constructeur privé.  Un constructeur privé empêche la classe d'être instanciée.  L'avantage de l'utilisation d'une classe statique est que le compilateur peut vérifier qu'aucun membre d'instance n'a été ajouté par erreur.  Le compilateur garantira que les instances de cette classe ne peuvent pas être créées.  
  
 Les classes statiques sont sealed et ne peuvent par conséquent pas être héritées.  Ils ne peuvent hériter d'aucune classe sauf <xref:System.Object>.  Les classes statiques ne peuvent pas contenir de constructeur d'instance ; toutefois, elles peuvent contenir un constructeur statique.  Les classes non statiques doivent également définir un constructeur statique si la classe contient des membres statiques qui requièrent une initialisation non triviale.  Pour plus d'informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## Exemple  
 Voici un exemple d'une classe statique qui contient deux méthodes qui convertissent la température de Celsius en Fahrenheit et de Fahrenheit en Celsius :  
  
 [!code-cs[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/static-classes-and-stati_1.cs)]  
  
## Membres statiques  
 Une classe non statique peut contenir des méthodes, des champs, des propriétés ou des événements statiques.  Le membre statique peut être appelé sur une classe même quand aucune instance de la classe n'a été créée.  Le membre statique est toujours accédé par le nom de classe, et non par le nom d'instance.  Une seule copie d'un membre statique existe, quel que soit le nombre d'instances de la classe créées.  Les méthodes et propriétés statiques ne peuvent pas accéder à des champs et des événements non statiques dans leur type contenant, et ils ne peuvent pas accéder à une variable d'instance de tout objet à moins qu'elle ne soit passée explicitement dans un paramètre de méthode.  
  
 Il est plus courant de déclarer une classe non statique avec certains membres statiques, que de déclarer une classe entière comme statique.  Deux utilisations courantes des champs statiques consistent à conserver un décompte du nombre d'objets ayant été instanciés ou à stocker une valeur qui doit être partagée par toutes les instances.  
  
 Les méthodes statiques peuvent être surchargées mais non substituées, car elles appartiennent à la classe, et non à une instance de la classe.  
  
 Bien qu'un champ ne puisse pas être déclaré comme `static const`, un champ [const](../../../csharp/language-reference/keywords/const.md) est essentiellement statique dans son comportement.  Il appartient au type, et pas aux instances du type.  Par conséquent, les champs const peuvent être accédés en utilisant la même notation `ClassName.MemberName` que celle utilisée pour les champs statiques.  Aucune instance d'objet n'est requise.  
  
 C\# ne prend pas en charge les variables locales statiques \(variables déclarées dans la portée de la méthode\).  
  
 Vous déclarez des membres de classe statique en utilisant le mot clé `static` avant le type de retour du membre, comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/static-classes-and-stati_2.cs)]  
  
 Les membres statiques sont initialisés avant que le membre statique fasse l'objet d'un accès pour la première fois, et avant que le constructeur statique, le cas échéant, soit appelé.  Pour accéder à un membre de classe statique, utilisez le nom de la classe au lieu d'un nom de variable pour spécifier l'emplacement du membre, comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/static-classes-and-stati_3.cs)]  
  
 Si votre classe contient des champs statiques, fournissez un constructeur statique qui les initialise lorsque la classe est chargée.  
  
 Un appel à une méthode statique génère une instruction d'appel en langage intermédiaire Microsoft \(MSIL\), alors qu'un appel à une méthode d'instance génère une instruction `callvirt`, qui vérifie également la présence de références d'objets Null.  Toutefois, la plupart du temps la différence de performance entre les deux n'est pas significative.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [statiques](../../../csharp/language-reference/keywords/static.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)   
 [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)