---
title: "Approfondissement du système de type commun"
description: "Approfondissement du système de type commun"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 7d7f869b07d7cf00ffa69da117aa199d1b6e8f20

---

# <a name="common-type-system-in-depth"></a>Approfondissement du système de type commun

Cette rubrique contient les sections suivantes qui explorent le système de type commun de manière approfondie :

* [Types dans .NET](#types-in-net)

* [Définitions de types](#type-definitions)

* [Membres de type](#type-members)

* [Caractéristiques des membres de type](#characteristics-of-type-members)


## <a name="types-in-net"></a>Types dans .NET

Tous les types dans .NET sont soit des types valeur, soit des types référence. 

Les types valeur sont des types de données dont les objets sont représentés par la valeur réelle de l'objet. Si une instance d'un type valeur est assignée à une variable, cette variable reçoit une copie actualisée de la valeur.

Les types référence sont des types de données dont les objets sont représentés par une référence (identique à un pointeur) à la valeur réelle de l'objet. Si un type référence est assigné à une variable, celle-ci référence (ou pointe vers) la valeur d'origine. Aucune copie n'est effectuée. 

Le système de type commun (CTS, Common Type System) dans .NET prend en charge les cinq catégories de types suivantes :

* [Classes](#classes)

* [Structures](#structures)

* [Énumérations](#enumerations)

* [Interfaces](#interfaces)

* [Délégués](#delegates)

### <a name="classes"></a>Classes

Une classe est un type référence qui peut être dérivé directement d’une autre classe et qui est implicitement dérivé de [System.Object](xref:System.Object). Une classe définit les opérations qu'un objet (qui est une instance de la classe) peut effectuer (méthodes, événements ou propriétés) et les données que l'objet contient (champs). Bien qu'une classe inclue généralement la définition et l'implémentation (contrairement aux interfaces, par exemple, qui contiennent uniquement la définition sans l'implémentation), elle peut comporter un ou plusieurs membres dépourvus d'implémentation.

Le tableau suivant décrit certaines des caractéristiques qu'une classe peut avoir. Chaque langage prenant en charge le runtime fournit un moyen d'indiquer qu'une classe ou qu'un membre d'une classe a une ou plusieurs de ces caractéristiques. Cependant, il se peut que des langages de programmation individuels qui ciblent .NET ne mettent pas toutes ces caractéristiques à disposition.

Caractéristique | Description
-------------- | -----------
sealed | Spécifie qu'une autre classe ne peut pas être dérivée de ce type.
implémente | Indique que la classe utilise une ou plusieurs interfaces en fournissant des implémentations des membres d'interface.
abstract | Indique que la classe ne peut pas être instanciée. Pour l'utiliser, vous devez dériver une autre classe de celle-ci.
hérite | Indique que des instances de la classe peuvent être utilisées partout où la classe de base est spécifiée. Une classe dérivée qui hérite d'une classe de base peut utiliser l'implémentation de n'importe quel membre public fourni par la classe de base, ou la classe dérivée peut remplacer l'implémentation des membres publics par sa propre implémentation.
exported ou not exported | Indique si une classe est visible à l'extérieur de l'assembly dans lequel elle est définie. Cette caractéristique s'applique uniquement aux classes de niveau supérieur, et pas aux classes imbriquées.

> [!NOTE]
> Une classe peut également être imbriquée dans une structure ou une classe parente. Les classes imbriquées ont également des caractéristiques de membre. Pour plus d’informations, consultez [Types imbriqués](#nested-types).

Les membres de classe sans implémentation sont des membres abstraits. Une classe qui possède un ou plusieurs membres abstraits est elle-même abstraite ; il n'est pas possible d'en créer de nouvelles instances. Certains langages qui ciblent le runtime vous permettent de marquer une classe comme abstraite même si aucun de ses membres n'est abstrait. Vous pouvez utiliser une classe abstraite lorsque vous voulez encapsuler un ensemble de fonctionnalités de base dont des classes dérivées peuvent hériter ou qu'elles peuvent substituer lorsque cela est approprié. Les classes qui ne sont pas abstraites sont qualifiées de classes concrètes.

Une classe peut implémenter n’importe quel nombre d’interfaces, mais elle ne peut hériter que d’une seule classe de base en plus de la classe [System.Object](xref:System.Object), de laquelle toutes les classes héritent implicitement. Toutes les classes doivent avoir au moins un constructeur qui initialise de nouvelles instances de la classe. Si vous ne définissez pas explicitement un constructeur, la plupart des compilateurs fourniront automatiquement un constructeur par défaut (sans paramètre).

### <a name="structures"></a>Structures

Une structure est un type valeur qui dérive implicitement de [System.ValueType](xref:System.ValueType) qui, à son tour, est dérivé de [System.Object](xref:System.Object). Une structure est très utile pour représenter des valeurs dont les besoins en ressources mémoire sont faibles, ainsi que pour passer des valeurs en tant que paramètres par valeur à des méthodes qui ont des paramètres fortement typés. Dans .NET, tous les types de données primitifs ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) et [UInt64](xref:System.UInt64)) sont définis comme structures.

Comme les classes, les structures définissent à la fois les données (les champs de la structure) et les opérations qui peuvent être exécutées sur ces données (les méthodes de la structure). Cela signifie que vous pouvez appeler des méthodes sur des structures, notamment les méthodes virtuelles définies sur les classes [System.Object](xref:System.Object) et [System.ValueType](xref:System.ValueType), ainsi que toute méthode définie sur le type valeur lui-même. En d'autres termes, les structures peuvent comporter des champs, des propriétés et des événements, ainsi que des méthodes statiques et non statiques. Vous pouvez créer des instances de structures, les passer en tant que paramètres, les stocker en tant que variables locales ou les stocker dans un champ d'un autre type valeur ou type référence. Les structures peuvent aussi implémenter des interfaces.

Les types valeur diffèrent également des classes par plusieurs aspects. Tout d’abord, bien qu’ils héritent implicitement de [System.ValueType](xref:System.ValueType), ils ne peuvent pas hériter directement de n’importe quel type. De même, tous les types valeur sont sealed, ce qui signifie qu'aucun autre type ne peut en être dérivé. De plus, ils ne nécessitent pas de constructeurs.

Pour chaque type valeur, le Common Language Runtime fournit un type boxed correspondant qui est une classe ayant le même état et le même comportement que le type valeur. Une instance d’un type valeur est boxed lorsqu’elle est passée à une méthode qui accepte un paramètre de type [System.Object](xref:System.Object). Elle est unboxed (c'est-à-dire reconvertie d'une instance d'une classe en instance d'un type valeur) lorsque le contrôle retourne d'un appel de méthode qui accepte un type valeur comme paramètre par référence. Certains langages imposent l'utilisation d'une syntaxe spéciale lorsque le type boxed est requis ; d'autres utilisent automatiquement le type boxed lorsqu'il est nécessaire. Lorsque vous définissez un type valeur, vous définissez le type boxed et le type unboxed.

### <a name="enumerations"></a>Énumérations

Une énumération (enum) est un type valeur qui hérite directement de [System.Enum](xref:System.Enum) et qui fournit des noms de remplacement pour les valeurs d’un type primitif sous-jacent. Un type énumération a un nom, un type sous-jacent qui doit être l’un des types d’entiers signés ou non signés intégrés (tels que [Byte](xref:System.Byte), [Int32](xref:System.Int32) ou [UInt64](xref:System.UInt64)) et un ensemble de champs. Les champs sont des champs statiques de type Literal, chacun représentant une constante. La même valeur peut être assignée à plusieurs champs. Dans ce cas, vous devez marquer l'une des valeurs comme valeur d'énumération primaire pour la réflexion et la conversion de chaînes.

Vous pouvez assigner une valeur du type sous-jacent à une énumération et vice-versa (aucun cast n'est requis par le runtime). Vous pouvez créer une instance d’une énumération et appeler les méthodes de [System.Enum](xref:System.Enum), ainsi que toute méthode définie sur le type sous-jacent de l’énumération. Cependant, il est possible que certains langages ne vous permettent pas de passer une énumération en tant que paramètre lorsqu'une instance du type sous-jacent est requise (ou vice versa).

Les restrictions supplémentaires suivantes s'appliquent aux énumérations : 

* Elles ne peuvent pas définir leurs propres méthodes.

* Elles ne peuvent pas implémenter d'interfaces.

* Elles ne peuvent pas définir des propriétés ou des événements.

* Elles ne peuvent pas être génériques, à moins qu'elles le soient uniquement parce qu'elles sont imbriquées dans un type générique. Par conséquent, une énumération ne peut pas avoir de paramètres de type propres. 

> [!NOTE]
> Les types imbriqués (y compris les énumérations) créés avec C# incluent les paramètres de type de tous les types génériques englobants, et sont donc génériques, même s’ils n’ont pas de paramètres de type propres. Pour plus d’informations, consultez la rubrique de référence [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])). 

L’attribut [FlagsAttribute](xref:System.FlagsAttribute) désigne un genre particulier d’énumération appelé « champ de bits ». Le runtime lui-même ne fait pas de distinction entre les énumérations traditionnelles et les champs de bits, mais votre langage pourrait le faire. Lorsque cette distinction est effectuée, les opérateurs binaires peuvent être utilisés sur les champs de bits, mais pas sur les énumérations, pour générer des valeurs sans nom. Les énumérations sont généralement utilisées pour des listes d'éléments uniques, tels que les jours de la semaine, des noms de pays ou de région, etc. Les champs de bits sont généralement utilisés pour des listes de qualités ou de quantités pouvant être utilisées en combinaison, telle que `Red And Big And Fast`.

L'exemple suivant montre comment utiliser les champs de bits et les énumérations traditionnelles.

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a>Interfaces

Une interface définit un contrat qui spécifie une relation « peut faire » ou « a un ». Les interfaces sont souvent utilisées pour implémenter des fonctionnalités, comme la comparaison et le tri (interfaces [IComparable](xref:System.IComparable) et [IComparable&lt;T&gt;](xref:System.IComparable%601)), le test de l’égalité (interface [IEquatable&lt;T&gt;](xref:System.IEquatable%601)) ou l’énumération d’éléments dans une collection (interfaces [IEnumerable](xref:System.Collections.IEnumerable) et [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601)). Les interfaces peuvent avoir des propriétés, des méthodes et des événements qui sont tous des membres abstraits, c'est-à-dire que bien que l'interface définisse les membres et leurs signatures, elle laisse le type qui implémente l'interface définir la fonctionnalité de chaque membre d'interface. En d'autres termes, toute classe ou structure qui implémente une interface doit fournir des définitions pour les membres abstraits déclarés dans l'interface. Une interface peut imposer à une classe ou à une structure d'implémentation d'implémenter une ou plusieurs autres interfaces.

Les restrictions suivantes s'appliquent aux interfaces : 

* Une interface peut être déclarée avec n'importe quelle accessibilité, mais les membres d'interface doivent tous avoir une accessibilité publique.

* Les interfaces ne peuvent pas définir de constructeurs.

* Les interfaces ne peuvent pas définir de champs.

* Les interfaces peuvent définir uniquement des membres d'instance. Elles ne peuvent pas définir des membres statiques.

Chaque langage doit fournir des règles de mappage d'une implémentation à l'interface qui nécessite le membre, car plusieurs interfaces peuvent déclarer un membre avec la même signature, et ces membres peuvent avoir des implémentations séparées.

### <a name="delegates"></a>Délégués

Les délégués sont des types référence qui jouent un rôle similaire à celui des pointeurs fonction en C++. Ils sont utilisés pour les gestionnaires d’événements et les fonctions de rappel dans .NET. Contrairement aux pointeurs fonction, les délégués sont de type sécurisé, sûr et vérifiable. Un type délégué peut représenter n'importe quelle méthode d'instance ou méthode statique ayant une signature compatible. 

Le paramètre d'un délégué est compatible avec le paramètre correspondant d'une méthode si le type de paramètre du délégué est plus restrictif que le type de paramètre de la méthode. En effet, cela garantit qu'un argument transmis au délégué peut être transmis à la méthode en toute sécurité.

De même, le type de retour d’un délégué est compatible avec le type de retour d’une méthode si le type de retour de la méthode est plus restrictif que le type de retour du délégué, car cela garantit que le cast de la valeur de retour de la méthode peut être effectué sans risque au type de retour du délégué.

Par exemple, un délégué ayant un paramètre de type [IEnumerable](xref:System.Collections.IEnumerable) et un type de retour [Object](xref:System.Object) peut représenter une méthode ayant un paramètre de type [Object](xref:System.Object) et une valeur de retour de type [IEnumerable](xref:System.Collections.IEnumerable). 

 On dit qu'un délégué est lié à la méthode qu'il représente. Outre cette liaison, un délégué peut être lié à un objet. L'objet représente le premier paramètre de la méthode, et est passé à cette dernière chaque fois que le délégué est appelé. Si la méthode est une méthode d'instance, l'objet dépendant est passé en tant que paramètre `this` implicite (`Me` en Visual Basic) ; si la méthode est statique, l'objet est passé en tant que premier paramètre formel de la méthode, et la signature du délégué doit correspondre aux paramètres restants. 
 
 Tous les délégués héritent de [System.MulticastDelegate](xref:System.MulticastDelegate), qui hérite de [System.Delegate](xref:System.Delegate). Les langages C# et Visual Basic n’autorisent pas l’héritage à partir de ces types. Ils fournissent à la place des mots clés pour la déclaration des délégués.
 
 Étant donné que les délégués héritent de [MulticastDelegate](xref:System.MulticastDelegate), un délégué dispose d’une liste d’appel, qui est la liste des méthodes représentées par le délégué et exécutées lorsque celui-ci est appelé. Toutes les méthodes de la liste reçoivent les arguments fournis lorsque le délégué est appelé.

> [!NOTE]
> La valeur de retour n'est pas définie pour un délégué dont la liste d'appel comprend plusieurs méthodes, même si le délégué dispose d'un type de retour.

Dans la plupart des cas, comme avec les méthodes de rappel, un délégué représente une seule méthode, et les mesures que vous devez prendre se limitent à la création et l'appel du délégué. 

Pour les délégués qui représentent plusieurs méthodes, .NET fournit les méthodes des classes de délégué [Delegate](xref:System.Delegate) et [MulticastDelegate](xref:System.MulticastDelegate) pour prendre en charge les opérations telles que l’ajout d’une méthode à la liste d’appel d’un délégué (méthode [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate))), la suppression d’une méthode (méthode [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate))) et l’obtention de la liste d’appel (méthode [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList)).

> [!NOTE]
> Il n’est pas nécessaire d’utiliser ces méthodes pour les délégués de gestionnaires d’événements en C# ou Visual Basic, car ces langages fournissent une syntaxe pour l’ajout et la suppression des gestionnaires d’événements.

## <a name="type-definitions"></a>Définitions de type

Une définition de type inclut les éléments suivants : 

* les attributs définis sur le type ;

* L'accessibilité du type (visibilité).

* le nom du type ;

* le type de base du type ;

* les interfaces implémentées par le type ;

* les définitions de chacun des membres du type.

### <a name="attributes"></a>Attributs

Les attributs fournissent des métadonnées définies par l'utilisateur supplémentaires. La plupart du temps, ils sont utilisés pour stocker les informations supplémentaires relatives à un type de l’assembly, ou pour modifier le comportement d’un membre de type dans l’environnement au moment du design ou dans l’environnement d’exécution. 

Les attributs sont eux-mêmes des classes qui héritent de [System.Attribute](xref:System.Attribute). Les langages qui prennent en charge l'utilisation d'attributs ont chacun leur propre syntaxe pour l'application d'attributs à un élément du langage. Les attributs peuvent être appliqués à presque n’importe quel élément de langage ; les éléments spécifiques auxquels un attribut peut être appliqué sont définis par l’attribut [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) qui est appliqué à cette classe d’attributs.

### <a name="type-accessibility"></a>Accessibilité des types

Tous les types ont un modificateur qui régit leur accessibilité à partir d'autres types. Le tableau suivant décrit les accessibilités de type prises en charge par le runtime.

Accessibilité | Description
------------- | -----------
public | Le type est accessible par tous les assemblys.
assembly | Le type est accessible uniquement à partir de cet assembly.

L'accessibilité d'un type imbriqué dépend de son domaine d'accessibilité, qui est déterminé par l'accessibilité déclarée du membre et le domaine d'accessibilité du type conteneur immédiat. Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.

Le domaine d’accessibilité d’un membre imbriqué `M` déclaré dans un type `T` à l’intérieur d’un programme `P` est défini de la manière suivante (en notant que `M` pourrait lui-même être un type) : 

* Si l'accessibilité déclarée de `M` est `public`, le domaine d'accessibilité de `M` correspond à celui de `T`.

* Si l'accessibilité déclarée de `M` est `protected internal`, le domaine d'accessibilité de `M` correspond à l'intersection du domaine d'accessibilité de `T` avec le texte de programme de `P` et le texte de programme de n'importe quel type dérivé de `T` déclaré en dehors de `P`.

* Si l'accessibilité déclarée de `M` est `protected`, le domaine d'accessibilité de `M` correspond à l'intersection du domaine d'accessibilité de `T` avec le texte de programme de `T` et n'importe quel type dérivé de `T`.

* Si l’accessibilité déclarée de `M` est `internal`, le domaine d’accessibilité de `M` correspond à l’intersection du domaine d’accessibilité de `T` avec le texte de programme de `P`.

* Si l'accessibilité déclarée de `M` est `private`, le domaine d'accessibilité de `M` correspond au texte de programme de `T`.

### <a name="type-names"></a>Noms de types

Le système de type commun (CTS, Common Type System) impose uniquement deux restrictions sur les noms : 

* Tous les noms sont encodés comme des chaînes de caractères Unicode (16 bits).

* Les noms ne peuvent pas incorporer la valeur (16 bits) 0x0000.

Toutefois, la plupart des langages imposent des restrictions supplémentaires sur les noms de types. Toutes les comparaisons sont effectuées octet par octet ; elles respectent donc la casse et sont indépendantes des paramètres régionaux.

Bien qu’un type puisse référencer des types d’autres modules et assemblys, il doit être entièrement défini à l’intérieur d’un seul module .NET. (Cependant, en fonction de la prise en charge du compilateur, il peut être divisé en plusieurs fichiers de code source.) Les noms de types doivent être uniques seulement à l'intérieur d'un espace de noms. Pour identifier complètement un type, le nom du type doit être qualifié par l'espace de noms qui contient l'implémentation du type.

### <a name="base-types-and-interfaces"></a>Types de base et interfaces

Un type peut hériter des valeurs et des comportements d'un autre type. Le système de type commun (CTS, Common Type System) ne permet pas à des types d'hériter de plusieurs types de base.

Un type peut implémenter n'importe quel nombre d'interfaces. Pour implémenter une interface, un type doit implémenter tous les membres virtuels de cette interface. Une méthode virtuelle peut être implémentée par un type dérivé et peut être appelée de manière statique ou dynamique.

## <a name="type-members"></a>Membres de type

Le runtime vous permet de définir les membres de votre type, ce qui spécifie le comportement et l'état d'un type. Les membres de type incluent les éléments suivants :

* [Champs](#fields)

* [Propriétés](#properties)

* [Méthodes](#methods)

* [Constructeurs](#constructors)

* [Événements](#events)

* [Types imbriqués](#nested-types)

### <a name="fields"></a>Champs

Un champ décrit et contient une partie de l'état du type. Les champs peuvent correspondre à n'importe quel type pris en charge par le runtime. La plupart du temps, les champs sont soit `private`, soit `protected`, de sorte qu'ils sont accessibles uniquement à partir de la classe ou d'une classe dérivée. Si la valeur d'un champ peut être modifiée en dehors de son type, un accesseur set de propriété est en général utilisé. Les champs exposés publiquement sont généralement en lecture seule et peuvent être de deux types : 

* Constantes, dont la valeur est assignée au moment du design. Ce sont des membres statiques d'une classe, bien qu'ils ne soient pas définis à l'aide du mot clé `static` (`Shared` en Visual Basic).

* Des variables en lecture seule, dont les valeurs peuvent être assignées dans le constructeur de classe.

L'exemple ci-dessous illustre ces deux utilisations de champs en lecture seule.

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a>Propriétés

Une propriété nomme une valeur ou un état du type et définit des méthodes pour obtenir ou définir la valeur de la propriété. Les propriétés peuvent être des types primitifs, des collections de types primitifs, des types définis par l'utilisateur ou des collections de types définis par l'utilisateur. Les propriétés sont souvent utilisées pour maintenir l'interface publique d'un type indépendante de la représentation réelle du type. Cela permet aux propriétés de refléter des valeurs qui ne sont pas directement stockées dans la classe (par exemple, lorsqu'une propriété retourne une valeur calculée) ou d'effectuer une validation avant que des valeurs soient assignées à des champs privés. L’exemple suivant illustre ce dernier modèle.

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

En plus d’inclure la propriété elle-même, le langage MSIL (Microsoft Intermediate Language) pour un type qui contient une propriété lisible inclut une méthode `get`*_nompropriété*, et le MSIL pour un type qui contient une propriété accessible en écriture inclut une méthode `set`*_nompropriété*.

### <a name="methods"></a>Méthodes

Une méthode décrit les opérations qui sont disponibles sur le type. La signature d'une méthode spécifie les types autorisés de tous ses paramètres et de sa valeur de retour.

Bien que la plupart des méthodes définissent le nombre précis de paramètres requis pour les appels de méthode, certaines méthodes acceptent un nombre variable de paramètres. Le dernier paramètre déclaré de ces méthodes est marqué avec l'attribut [ParamArrayAttribute](xref:System.ParamArrayAttribute). Les compilateurs de langage fournissent généralement un mot clé, tel que `params` en C# et `ParamArray` en Visual Basic, qui rendent l’utilisation explicite de [ParamArrayAttribute](xref:System.ParamArrayAttribute) inutile.

### <a name="constructors"></a>Constructeurs

Un constructeur est un genre de méthode particulier qui crée de nouvelles instances d'une classe ou d'une structure. Comme n'importe quelle autre méthode, un constructeur peut inclure des paramètres ; toutefois, les constructeurs n'ont pas de valeur de retour (en d'autres termes, ils retournent `void`). 

Si le code source d'une classe ne définit pas explicitement un constructeur, le compilateur inclut un constructeur par défaut (sans paramètre). Toutefois, si le code source d’une classe définit uniquement des constructeurs paramétrables, le compilateur C# ne génère pas de constructeur sans paramètre.

Si le code source d'une structure définit des constructeurs, ils doivent être paramétrables ; une structure ne peut pas définir un constructeur (sans paramètre) par défaut et les compilateurs ne génèrent pas de constructeur sans paramètre pour les structures ou les autres types valeurs. Tous les types valeurs disposent d'un constructeur implicite par défaut. Ce constructeur est implémenté par le Common Language Runtime et initialise tous les champs de la structure avec leurs valeurs par défaut. 

### <a name="events"></a>Événements

Un événement définit un incident auquel il est possible de répondre, et définit les méthodes permettant de s'abonner à l'événement, d'annuler cet abonnement et de déclencher l'événement. Les événements sont souvent utilisés pour signaler d'autres types de changements d'état.

### <a name="nested-types"></a>Types imbriqués

Un type imbriqué est un type qui est un membre d'un autre type. Un type imbriqué doit être fortement couplé avec le type qui le contient et ne doit pas être utilisé en tant que type à usage général. Ceux-ci sont utiles lorsque le type de déclaration utilise et crée des instances du type imbriqué et que l'utilisation du type imbriqué n'est pas exposée dans des membres publics.

Certains développeurs éprouvent des difficultés à appréhender correctement les types imbriqués. Il faut savoir qu'ils ne doivent pas être publiquement visibles sauf s'il existe une bonne raison à cela. Dans une bibliothèque bien conçue, les développeurs doivent rarement avoir à utiliser des types imbriqués pour instancier des objets ou déclarer des variables.

## <a name="characteristics-of-type-members"></a>Caractéristiques des membres de type

Le système de type commun (CTS, Common Type System) permet aux membres de type d'avoir diverses caractéristiques ; toutefois, les langages ne doivent pas obligatoirement prendre en charge toutes ces caractéristiques. Le tableau suivant décrit les caractéristiques des membres.

Caractéristique | Applicable à | Description
-------------- | ------------ | -----------
abstract | Méthodes, propriétés et événements | Le type n'assure pas l'implémentation de la méthode. Les types qui héritent de méthodes abstraites ou qui en implémentent doivent fournir une implémentation pour la méthode. Une exception : le type dérivé est lui-même un type abstrait. Toutes les méthodes abstraites sont virtuelles.
private | Tous | Accessible uniquement à partir du même type que le membre ou à l'intérieur d'un type imbriqué.
family | Tous | Accessible à partir du même type que le membre et à partir des types dérivés qui en héritent.
assemby | Tous | Accessible uniquement dans l'assembly dans lequel le type est défini.
family et assembly | Tous | Accessible uniquement à partir des types qui se qualifient pour un accès family et assembly.
family ou assembly | Tous | Accessible uniquement à partir des types qui se qualifient pour un accès family ou assembly.
public | Tous | Accessible à partir de n'importe quel type.
final | Méthodes, propriétés et événements | La méthode virtuelle ne peut pas être substituée dans un type dérivé.
initialize-only | Champs | La valeur peut seulement être initialisée et ne peut pas être écrite après initialisation.
instance | Champs, méthodes, propriétés et événements | Si un membre n’est pas marqué comme `static` (C#), `Shared` (Visual Basic), `virtual` (C#) ou `Overridable` (Visual Basic), il est membre d’instance (il n’y a pas de mot clé d’instance). La mémoire comptera autant de copies de tels membres que d'objets qui les utilisent.
littéral | Champs | La valeur assignée au champ est une valeur fixe, connue au moment de la compilation, d'un type valeur intégré. Les champs de type Literal sont parfois qualifiés de constantes.
newslot ou override | Tous | Définit la façon dont le membre interagit avec des membres hérités ayant la même signature : `newslot` masque les membres hérités ayant la même signature ; `override` remplace la définition d’une méthode virtuelle héritée. La valeur par défaut est newslot.
statique | Champs, méthodes, propriétés et événements | Le membre appartient au type sur lequel il est défini, et non à une instance particulière du type ; le membre existe même si une instance du type n'est pas créée, et il est partagé entre toutes les instances du type.
virtual | Méthodes, propriétés et événements | La méthode peut être implémentée par un type dérivé et peut être appelée de manière statique ou dynamique. Si un appel dynamique est utilisé, le type de l'instance qui effectue l'appel au moment de l'exécution détermine quelle implémentation de la méthode est appelée (plutôt que le type connu au moment de la compilation). Pour appeler une méthode virtuelle de manière statique, un cast en un type qui utilise la version désirée de la méthode devra éventuellement être effectué sur la variable.

### <a name="overloading"></a>Surcharge

Chaque membre de type a une signature unique. Les signatures de méthode sont composées du nom de la méthode, d'une liste de paramètres (l'ordre et les types des arguments de la méthode). Plusieurs méthodes du même nom peuvent être définies dans un type à condition que leurs signatures diffèrent. Lorsque plusieurs méthodes du même nom sont définies, la méthode est dite surchargée. Par exemple, dans [System.Char](xref:System.Char), la méthode `IsDigit` est surchargée. Une seule méthode accepte un [Char](xref:System.Char). L’autre méthode prend un [String](xref:System.String) et un [Int32](xref:System.Int32). 

> [!NOTE]
> Le type de retour n’est pas considéré comme une partie de la signature d’une méthode. En d'autres termes, les méthodes ne peuvent pas être surchargées si seul le type de retour les différencie.

### <a name="inheriting-overriding-and-hiding-members"></a>Héritage, substitution et masquage de membres

Un type dérivé hérite de tous les membres de son type de base ; c'est-à-dire que ces membres sont définis sur le type dérivé et disponibles pour celui-ci. Le comportement ou les qualités de membres hérités peuvent être modifiés de deux manières : 

* Un type dérivé peut masquer un membre hérité en définissant un nouveau membre avec la même signature. Cela permet notamment de rendre privé un membre précédemment public ou de définir un nouveau comportement pour une méthode héritée marquée comme `final`.

* Un type dérivé peut substituer une méthode virtuelle héritée. La méthode de substitution fournit une nouvelle définition de la méthode qui sera appelée en fonction du type de la valeur au moment de l'exécution et non du type de la variable connue au moment de la compilation. Une méthode peut substituer une méthode virtuelle uniquement si la méthode virtuelle n'est pas marquée comme `final` et si la nouvelle méthode est au moins aussi accessible que la méthode virtuelle.

## <a name="see-also"></a>Voir aussi

[Conversion de type dans le .NET Framework](type-conversion.md)


<!--HONumber=Nov16_HO1-->


