---
title: "Initiation à .NET"
description: "Initiation à .NET"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 10/05/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: be774ae1291def36baafffbf2f717cf98565cd60
ms.openlocfilehash: fba870a93784b579da1065a07d82974951ac7e28

---

# <a name="net-primer"></a>Initiation à .NET

> Consultez les [didacticiels « Bien démarrer avec .NET Core »](../core/getting-started.md) pour savoir comment créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.

.NET est une plateforme de développement généraliste. Elle peut être utilisée pour n’importe quel type d’application ou charge de travail faisant appel à des solutions généralistes. Elle comporte plusieurs fonctionnalités clés susceptibles de séduire de nombreux développeurs, notamment la gestion automatique de la mémoire et les langages de programmation modernes, qui facilitent sensiblement la création d’applications de haute qualité. .NET met à votre disposition un environnement de programmation général avec de nombreuses fonctionnalités pratiques, tout en donnant un accès aux API et à la mémoire natives.

Plusieurs implémentations de .NET sont disponibles, basées sur des [normes .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) ouvertes qui spécifient les principes fondamentaux de la plateforme. Elles sont optimisées individuellement pour différents types d’application (par exemple, bureau, mobile, jeu, cloud) et prennent en charge plusieurs processeurs (par exemple, x86/x64, ARM) et systèmes d’exploitation (par exemple, Windows, Linux, iOS, Android, Mac OS). L’open source est également une partie importante de l’écosystème .NET, avec plusieurs implémentations .NET et de nombreuses bibliothèques disponibles sous licences certifiées OSI.

Consultez la [Vue d’ensemble des implémentations .NET](../about/products.md) pour déterminer toutes les différentes éditions de .NET qui sont disponibles, à la fois chez Microsoft et d’autres éditeurs.

Cette initiation doit vous permettre de comprendre certains concepts clés de la plateforme .NET et vous indiquer des ressources supplémentaires pour chaque rubrique donnée. À la fin de celle-ci, vous disposerez de suffisamment d’informations pour pouvoir reconnaître les termes et les concepts significatifs de la plateforme .NET et pour savoir comment approfondir votre connaissance en la matière. 

## <a name="a-stroll-through-net"></a>Tour d’horizon de .NET

Comme tout framework de développement d’applications avancé et mature, .NET offre de nombreuses fonctionnalités utiles qui facilitent le travail du développeur et visent à rendre l’écriture de code plus expressive et plus puissante. Cette section décrit les principes de base des fonctionnalités les plus importantes et pointe sur des discussions plus détaillées si nécessaire. À la fin de ce tour d’horizon, vous disposerez de suffisamment d’informations pour pouvoir lire les exemples de notre dépôt GitHub et d’autre code, et pour comprendre de quoi il retourne.

*   [Langages de programmation](#programming-languages)
*   [Gestion automatique de la mémoire](#automatic-memory-management)
*   [Cohérence des types](#type-safety)
*   [Délégués et expressions lambda](#delegates-and-lambdas)
*   [Types génériques (Génériques)](#generic-types-generics)
*   [LINQ (Language Integrated Query)](#language-integrated-query-linq)
*   [Programmation asynchrone](#async-programming)
*   [Interopérabilité native](#native-interoperability)
*   [Code unsafe](#unsafe-code)

### <a name="programming-languages"></a>Langages de programmation

En qualité de développeur, vous pouvez choisir n’importe quel langage de programmation qui prend en charge .NET pour créer votre application. Comme .NET fournit l’indépendance et l’interopérabilité des langages, vous pouvez interagir avec d’autres applications et composants .NET, quel que soit le langage utilisé pour leur développement.

Les langages qui vous permettent de développer des applications pour la plateforme .NET respectent la [Spécification CLI (Common Language Infrastructure)](https://www.visualstudio.com/en-us/mt639507).

Les langages Microsoft que .NET prend en charge sont notamment C#, F# et Visual Basic. 

* C# est simple, puissant, de type sécurisé et orienté objet, tout en conservant l’expressivité et l’élégance des langages de style C. Les utilisateurs familiarisés avec le langage C et les langages similaires auront peu de difficultés à s’adapter à C#.

* F# est un langage de programmation multiplateforme et fonctionnel qui prend également en charge la programmation orientée objet et impérative traditionnelle.

* Visual Basic est un langage facile à apprendre que vous pouvez utiliser pour créer une variété d’applications qui s’exécutent sur .NET.

> [!NOTE]
> Dans la version actuelle de .NET Core, C# est entièrement pris en charge par tous les outils Microsoft.  F# est pris en charge dans le SDK .NET Core, mais n’a pas encore les outils Visual Studio.  La prise en charge de Visual Basic pour le SDK et les outils Visual Studio sera bientôt disponible.

### <a name="automatic-memory-management"></a>Gestion automatique de la mémoire

Le garbage collection est la fonctionnalité .NET la mieux connue. Les développeurs n’ont pas besoin de gérer activement la mémoire, bien qu’il existe des mécanismes pour fournir plus d’informations au récupérateur de mémoire. C# inclut le mot clé `new` pour allouer de la mémoire en termes d’un type particulier et le mot clé `using` pour définir la portée de l’utilisation de l’objet. Le récupérateur de mémoire opère avec une approche différée de la gestion de la mémoire, préférant le débit de l’application à la collecte immédiate de la mémoire.

Les deux lignes suivantes allouent de la mémoire :

```cs
var title = ".NET Primer";
var list = new List<string>;

```

Il n’existe aucun mot clé analogue pour libérer de la mémoire, car la libération de mémoire se produit automatiquement quand le récupérateur de mémoire réclame la mémoire dans son exécution planifiée.

Les variables de méthode sont normalement hors de portée à la fin d’une méthode, point auquel elles peuvent être récupérées. Toutefois, vous pouvez indiquer au récupérateur de mémoire qu’un objet en particulier est hors de portée avant la fin de la méthode à l’aide de l’instruction `using`.

```cs
using(FileStream stream = GetFileStream(context))
{
    //operations on the stream
}

```

Une fois que le bloc `using` a terminé, le récupérateur de mémoire sait que l’objet `stream` dans l’exemple ci-dessus peut être collecté et sa mémoire récupérée.

Une des fonctionnalités les moins évidentes et pourtant assez importantes que le récupérateur de mémoire active est la sûreté de la mémoire. L’invariant de la sûreté de la mémoire est très simple : un programme a une mémoire sécurisée s’il accède uniquement à la mémoire qui a été allouée (et non libérée). Les pointeurs non résolus sont toujours des bogues et leur suivi est souvent très difficile.

Le runtime .NET fournit des services supplémentaires pour assurer la sûreté de la mémoire, qui ne sont pas naturellement offerts par un récupérateur de mémoire. Il garantit que les programmes n’indexent pas à la fin d’un tableau ou accèdent à un champ fantôme à la fin d’un objet.

L’exemple suivant lève une exception en raison de la sûreté de la mémoire.

```cs
int[] numbers = new int[42];
int number = numbers[42]; // will throw (indexes are 0-based)

```

### <a name="type-safety"></a>Cohérence des types

Les objets sont alloués en termes de types. Les seules opérations autorisées pour un objet donné et la mémoire qu’il consomme sont celles de son type. Un type `Dog` peut avoir des méthodes `Jump` et `WagTail`, mais probablement pas une méthode `SumTotal`. Un programme peut appeler uniquement les méthodes déclarées d’un type donné. Tous les autres appels entraînent une erreur au moment de la compilation ou une exception au moment de l’exécution (en cas d’utilisation de fonctionnalités dynamiques ou du type `object`).

Les langages .NET sont orientés objet, avec des hiérarchies de classes de base et dérivées. Le runtime .NET autorise uniquement les casts et les appels d’objet qui s’alignent sur la hiérarchie d’objets. N’oubliez pas que chaque type défini dans un langage .NET dérive du type `object` de base.

```cs
Dog dog = Dog.AdoptDog(); // Returns a Dog type
Pet pet = (Pet)dog; // Dog derives from Pet
pet.ActCute();
Car car = (Car)dog; // will throw - no relationship between Car and Dog
object temp = (object)dog; // legal - a Dog is an object
car = (Car)temp; // will throw - the runtime isn't fooled
car.Accelerate() // the dog won't like this, nor will the program get this far

```

La cohérence des types est également utilisée pour aider à appliquer l’encapsulation en garantissant la fidélité des mots clés d’accesseur. Les mots clés d’accesseur sont des artefacts qui contrôlent l’accès aux membres d’un type donné par un autre code. Ils servent généralement à différentes sortes de données dans un type utilisées pour gérer son comportement.

```cs
Dog dog = Dog._nextDogToBeAdopted; // will throw - this is a private field

```

Certains langages .NET prennent en charge l’**inférence de type**. L’inférence de type signifie que le compilateur déduit le type de l’expression à gauche à partir de l’expression à droite. Cela ne signifie pas que la cohérence des types est interrompue ou évitée. Le type résultant **a** un type fort avec tout ce que cela implique. Réécrivons les deux premières lignes de l’exemple précédent pour introduire l’inférence de type. Notez que le reste de l’exemple est complètement identique.

```cs
  var dog = Dog.AdoptDog();
  var pet = (Pet)dog;
  pet.ActCute();
  Car car = (Car)dog; // will throw - no relationship between Car and Dog
  object temp = (object)dog; // legal - a Dog is an object
  car = (Car)temp; // will throw - the runtime isn't fooled
  car.Accelerate() // the dog won't like this, nor will the program get this far

```

### <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Les délégués sont comme des pointeurs de fonction C++, à la grande différence qu’ils sont de type sécurisé. Ils représentent une sorte de méthode déconnectée au sein du système de type CLR. Les méthodes régulières sont attachées à une classe et peuvent être appelées directement uniquement par des conventions d’appel statiques ou d’instance.

Les délégués sont utilisés dans diverses API et emplacements de l’environnement .NET, en particulier dans les expressions lambda, qui sont la pierre angulaire de LINQ.

Pour en savoir plus sur ce sujet, lisez le document [Délégués et expressions lambda](delegates-lambdas.md).

### <a name="generic-types-generics"></a>Types génériques (Génériques)

Les types génériques, ou les « génériques », sont une fonctionnalité qui a été ajoutée dans .NET Framework 2.0. En bref, les génériques permettent au programmeur d’introduire un « paramètre de type » quand il désigne leurs classes qui permettra au code client (les utilisateurs du type) de spécifier le type exact à utiliser à la place du paramètre de type.

Les génériques ont été ajoutés pour aider les programmeurs à implémenter des structures de données génériques. Avant leur arrivée, pour qu’un type _liste_, par exemple, soit générique, il fallait utiliser des éléments qui étaient de type _objet_. Cela entraînait des variations de performances ainsi que des problèmes sémantiques, sans oublier les possibles erreurs d’exécution subtiles. Les erreurs les plus connues dans cette dernière catégorie interviennent quand une structure de données contient, par exemple, des entiers et des chaînes et qu’une exception _InvalidCastException_ est levée lors de l’utilisation des membres de la liste.

L’exemple ci-dessous montre une exécution de programme de base utilisant une instance des types @System.Collections.Generic.List%601.

```cs
using System;
using System.Collections.Generic;

namespace GenericsSampleShort {
    public static void Main(string[] args){
        // List<string> is the client way of specifying the actual type for the type parameter T
        List<string> listOfStrings = new List<string> { "First", "Second", "Third" };

        // listOfStrings can accept only strings, both on read and write.
        listOfStrings.Add("Fourth");

        // Below will throw a compile-time error, since the type parameter
        // specifies this list as containing only strings.
        listOfStrings.Add(1);

    }
}

```

Pour plus d’informations, consultez l’article [Vue d’ensemble des types génériques (Génériques)](generics.md).

### <a name="async-programming"></a>Programmation asynchrone

La programmation asynchrone est un concept de première classe dans .NET, avec prise en charge asynchrone dans le runtime, les bibliothèques de framework et les constructions de langage .NET. En interne, ils sont basés sur des objets (comme `Task`) qui tirent parti du système d’exploitation pour effectuer aussi efficacement que possible des tâches utilisant des E/S.

Pour en savoir plus sur la programmation asynchrone dans .NET, commencez par la [Vue d’ensemble d’Async](async.md).

### <a name="language-integrated-query-linq"></a>LINQ (Language-Integrated Query)

LINQ est un ensemble puissant de fonctionnalités pour C# et VB qui vous permettent d’écrire du code simple et déclaratif pour l’exploitation des données. Les données peuvent se présenter sous plusieurs formes (comme des objets en mémoire, dans une base de données SQL ou un document XML), mais le code LINQ que vous écrivez généralement n’est pas différent pour chaque source de données !

Pour en savoir plus et obtenir des exemples, consultez [LINQ (Language Integrated Query)](using-linq.md).

### <a name="native-interoperability"></a>Interopérabilité native

Chaque système d’exploitation en cours d’utilisation prend en charge un grand nombre de plateformes pour diverses tâches de programmation. .NET offre plusieurs moyens de tirer parti de ces API. Collectivement, cette prise en charge est appelée « interopérabilité native » et, dans cette section, nous allons voir comment accéder aux API natives à partir du code managé .NET.

Le principal moyen d’effectuer une interopérabilité native est via l’« appel de code non managé » ou P/Invoke, en forme abrégée. Cette prise en charge dans .NET Core est disponible sur les plateformes Linux et Windows. Un autre moyen de faire une interopérabilité native sur Windows uniquement est connu sous le nom de « COM Interop », utilisé pour travailler avec des [composants COM](https://msdn.microsoft.com/library/bwa2bx93.aspx) dans du code managé. Il est basé sur l’infrastructure de P/Invoke, mais fonctionne légèrement différemment.

Une grande partie de la prise en charge d’interopérabilité dans Mono (et donc dans Xamarin) pour Java et Objective-C est générée de la même façon, autrement dit, ils utilisent les mêmes principes.

Pour en savoir plus, lisez le document [Interopérabilité native](native-interop.md).

### <a name="unsafe-code"></a>Code unsafe

Le CLR permet d’accéder à la mémoire native et d’effectuer une opération arithmétique de pointeur via du code `unsafe`. Ces opérations sont nécessaires pour certains algorithmes et pour l’interopérabilité du système. L’utilisation de code unsafe, bien que puissante, est déconseillée, sauf si elle est nécessaire pour assurer l’interopérabilité avec les API système ou implémenter l’algorithme le plus efficace. Le code unsafe peut ne pas s’exécuter de la même façon dans différents environnements et perd les avantages d’un récupérateur de mémoire et de la cohérence des types. Il est recommandé de restreindre et centraliser le code unsafe autant que possible, et de tester ce code de manière approfondie.

La méthode `ToString()` de la [classe StringBuilder](https://github.com/dotnet/coreclr/blob/master/src/mscorlib/src/System/Text/StringBuilder.cs#L327) illustre comment l’utilisation de code `unsafe` peut implémenter efficacement un algorithme en déplaçant directement des segments de mémoire :

```cs
public override String ToString() {
          Contract.Ensures(Contract.Result<String>() != null);

          VerifyClassInvariant();

          if (Length == 0)
              return String.Empty;

          string ret = string.FastAllocateString(Length);
          StringBuilder chunk = this;
          unsafe {
              fixed (char* destinationPtr = ret)
              {
                  do
                  {
                      if (chunk.m_ChunkLength > 0)
                      {
                          // Copy these into local variables so that they are stable even in the presence of ----s (hackers might do this)
                          char[] sourceArray = chunk.m_ChunkChars;
                          int chunkOffset = chunk.m_ChunkOffset;
                          int chunkLength = chunk.m_ChunkLength;

                          // Check that we will not overrun our boundaries.
                          if ((uint)(chunkLength + chunkOffset) <= ret.Length && (uint)chunkLength <= (uint)sourceArray.Length)
                          {
                              fixed (char* sourcePtr = sourceArray)
                                  string.wstrcpy(destinationPtr + chunkOffset, sourcePtr, chunkLength);
                          }
                          else
                          {
                              throw new ArgumentOutOfRangeException("chunkLength", Environment.GetResourceString("ArgumentOutOfRange_Index"));
                          }
                      }
                      chunk = chunk.m_ChunkPrevious;
                  } while (chunk != null);
              }
          }
          return ret;
      }

```

## <a name="notes"></a>Notes

Le terme « runtime .NET » est utilisé dans le document pour englober les différentes implémentations de .NET, comme CLR, Mono, IL2CPP et d’autres. Les noms plus spécifiques sont utilisés uniquement si nécessaire.

Ce document n’est pas historique, mais il décrit la plateforme .NET dans son état actuel. Cela n’a pas d’importance qu’une fonctionnalité .NET ait toujours été disponible ou ait été introduite seulement récemment, nous exposons uniquement ce qui est suffisamment important pour le souligner et en discuter.



<!--HONumber=Nov16_HO1-->


