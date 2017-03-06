---
title: "Délégués et expressions lambda"
description: "Délégués et expressions lambda"
keywords: .NET, .NET Core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 1dbe9c72999c14e45910310eb0bbc91ebe9f1e4a
ms.lasthandoff: 03/02/2017

---

# <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Les délégués définissent un type, qui spécifie la signature d’une méthode particulière. Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée. L’exemple suivant montre l’utilisation des délégués.

```cs
public class Program
{

  public delegate string Reverse(string s);

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Reverse rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}

```

*   Sur la ligne 4, nous créons un type délégué d’une certaine signature, dans notre exemple, une méthode qui accepte un paramètre de chaîne, puis renvoie un paramètre de chaîne.
*   Sur la ligne 6, nous définissons l’implémentation du délégué en fournissant une méthode qui a exactement la même signature.
*   Sur la ligne 13, la méthode est attribuée à un type conforme au délégué `Reverse`.
*   Enfin, sur la ligne 15, nous appelons le délégué en passant une chaîne à inverser.

Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer. Il s’agit de `Func<>`, `Action<>` et `Predicate<>`. Ils peuvent être utilisés à plusieurs endroits dans les API .NET, sans avoir à définir de nouveaux types délégués. Bien sûr, il existe certaines différences entre ces trois types, comme vous pouvez le constater dans leurs signatures, qui sont principalement liées à la manière dont ils doivent être utilisés :

*   `Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué.
*   `Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent. C’est le cas, par exemple, des projections.
*   `Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué. Il peut également être écrit comme un `Func<T, bool>`.

Nous pouvons maintenant reprendre notre exemple ci-dessus et le réécrire à l’aide du délégué `Func<>` au lieu d’un type personnalisé. Le programme continue à s’exécuter exactement de la même façon.

```cs
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}

```

Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode Main(). C’est pourquoi .NET Framework 2.0 a introduit le concept des **délégués anonymes**. Grâce à eux, vous pouvez créer des délégués « inline », sans avoir à spécifier un autre type ou méthode. Vous insérez simplement la définition du délégué là où vous en avez besoin.

En guise d’exemple, nous allons utiliser notre délégué anonyme pour filtrer une liste uniquement sur les nombres pairs et les imprimer dans la console.

```cs
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}

```

Notez les lignes en surbrillance. Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué. Mais au lieu d’être une définition séparée, nous l’avons introduit _ad hoc_ dans notre appel à la méthode `FindAll()` du type `List<T>`.

Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile. C’est là que les **expressions lambda** interviennent.

Les expressions lambda ont été initialement introduites dans C# 3.0 comme l’un des principaux blocs de construction de la requête LINQ (Language-Integrated Query). Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués. Elles déclarent une signature et un corps de méthode, mais n’ont pas d’identité formelle propre, sauf si elles sont attribuées à un délégué. Contrairement aux délégués, elles peuvent être directement attribuées comme côté gauche de l’inscription d’événement, ou dans plusieurs clauses et méthodes Linq.

Dans la mesure où une expression lambda est simplement une autre façon de spécifier un délégué, nous pouvons réécrire l’exemple ci-dessus pour utiliser une expression lambda au lieu d’un délégué anonyme.

```cs
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(i => i % 2 == 0);

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}

```

Si vous jetez un œil aux lignes en surbrillance, vous pouvez voir à quoi ressemble une expression lambda. Là encore, il s’agit simplement d’une syntaxe **très** pratique pour l’utilisation des délégués. Par conséquent, ce qui se passe en coulisses est très proche de ce qui se passe avec le délégué anonyme.

Comme les expressions lambda sont juste des délégués, elles peuvent servir de gestionnaire d’événements sans aucun problème, comme l’illustre l’extrait de code suivant.

```cs
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}

```

## <a name="further-reading-and-resources"></a>Ressources et informations supplémentaires

*   [Délégués](https://msdn.microsoft.com/library/ms173171.aspx)
*   [Fonctions anonymes](https://msdn.microsoft.com/library/bb882516.aspx)
*   [Expressions lambda](https://msdn.microsoft.com/library/bb397687.aspx)

