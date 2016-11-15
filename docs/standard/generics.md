---
title: "Vue d’ensemble des types génériques (Génériques)"
description: "Vue d’ensemble des types génériques (Génériques)"
keywords: .NET, .NET Core
author: kuhlenh
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
translationtype: Human Translation
ms.sourcegitcommit: 5b1a76c011b95db3ff5c4b4e01556f79c45fb369
ms.openlocfilehash: 5dcb9d10aeded8c5e8956c4b99ba9675311a787a

---

# <a name="generic-types-generics-overview"></a>Vue d’ensemble des types génériques (Génériques)

Nous utilisons les génériques tout le temps en C#, implicitement ou explicitement. Quand vous utilisez LINQ dans C#, avez-vous déjà remarqué que vous utilisez IEnumerable<T> ? Sinon, si vous avez déjà vu un exemple en ligne d’un « référentiel générique » pour communiquer avec les bases de données à l’aide d’Entity Framework, avez-vous remarqué que la plupart des méthodes retournent IQueryable<T> ? Vous vous êtes peut-être demandé ce que signifie le **T** dans ces exemples et pourquoi il s’y trouve ?

Présentés pour la première fois dans le .NET Framework 2.0, les génériques impliquaient des modifications du langage C# et du Common Language Runtime (CLR). Les **génériques** sont essentiellement un « modèle de code » qui permet aux développeurs de définir des structures de données de [type sécurisé](https://msdn.microsoft.com/library/hbzz1a9a.aspx) sans se limiter à un type de données réel. Par exemple, `List<T>` est une [collection générique](https://msdn.microsoft.com/library/System.Collections.Generic.aspx) qui peut être déclarée et utilisée avec n’importe quel type : `List<int>`, `List<string>`, `List<Person>`, etc.

Donc, quelle est l’idée ? Pourquoi les génériques sont-ils utiles ? Pour le comprendre, nous devons jeter un œil à une classe spécifique avant et après l’ajout des génériques. Observons `ArrayList`. Dans C# 1.0, les éléments `ArrayList` étaient de type `object`. C’est-à-dire que n’importe quel élément ajouté était converti en `object` en mode silencieux. La même chose se produit quand on lit des éléments de la liste (ce processus est appelé [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) et unboxing, respectivement). Le boxing et l’unboxing ont un impact sur les performances. Par ailleurs, il est impossible de déterminer au moment de la compilation le type réel des données de la liste. Cela fragilise parfois le code. Les génériques résolvent ce problème en fournissant des informations supplémentaires sur le type de données que contient chaque instance de liste. Pour faire simple, vous pouvez ajouter uniquement des entiers dans `List<int>` et uniquement des personnes dans `List<Person>`, etc..

Les génériques sont également disponibles au moment de l’exécution, ou **réifiés**. Cela signifie que le runtime sait quel type de structure de données vous utilisez et peut le stocker dans la mémoire plus efficacement.

Voici un petit programme qui illustre à quel point il est efficace de connaître le type de structure de données au moment de l’exécution :

```cs
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }

```

Ce programme produit la sortie suivante :

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms

```

La première chose que vous remarquez ici est que le tri de la liste générique est beaucoup plus rapide que celui de la liste non générique. Vous pouvez également noter que le type de la liste générique est différent ([System.Int32]) alors que le type de la liste non générique est généralisé. Comme le runtime sait que le générique `List<int>` est de type int, il peut stocker les éléments de liste dans un tableau d’entiers sous-jacent dans la mémoire, alors que le non générique `ArrayList` doit effectuer un cast de chaque élément de liste en objet stocké dans un tableau d’objets dans la mémoire. Comme le montre cet exemple, les casts supplémentaires prennent du temps et ralentissent le tri de la liste.

La dernière chose utile liée au fait que le runtime connaisse le type de votre générique est une meilleure expérience de débogage. Quand vous déboguez un générique en C#, vous connaissez le type de chaque élément dans votre structure de données. Sans les génériques, vous ne pourriez pas connaître le type de chaque élément.

## <a name="further-reading-and-resources"></a>Ressources et informations supplémentaires

*   [Présentation des génériques C#](https://msdn.microsoft.com/library/ms379564.aspx)
*   [Guide de programmation C# - Génériques](https://msdn.microsoft.com/library/512aeb7t.aspx)



<!--HONumber=Nov16_HO1-->


