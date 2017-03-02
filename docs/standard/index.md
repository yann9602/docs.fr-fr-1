---
title: "À propos de .NET"
description: En savoir plus sur la plateforme .NET.
keywords: .NET, .NET Core
author: richlander
ms.author: ronpet
ms.date: 10/31/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: be44dce8181be45f6d73fcf498a873fb94aa56a6
ms.lasthandoff: 03/02/2017

---

# <a name="net-platform-guide"></a>Guide de la plateforme .NET

> [!NOTE]
Cet article va être réécrit.

> Consultez les [didacticiels « Bien démarrer avec .NET Core »](../core/getting-started.md) pour savoir comment créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.

.NET est une plateforme de développement généraliste. Elle peut être utilisée pour n’importe quel type d’application ou charge de travail faisant appel à des solutions généralistes. Elle comporte plusieurs fonctionnalités clés susceptibles de séduire de nombreux développeurs, notamment la gestion automatique de la mémoire et les langages de programmation modernes, qui facilitent sensiblement la création d’applications de haute qualité. .NET met à votre disposition un environnement de programmation général avec de nombreuses fonctionnalités pratiques, tout en donnant un accès précis aux API et mémoire natives.

C#, F# et Visual Basic sont des langages reconnus qui ciblent la plateforme .NET et s’appuient sur celle-ci. Des fonctionnalités clés telles que le modèle de programmation asynchrone, Language Integrated Query, les types génériques et la réflexion de système de type font la renommée des langages .NET. En outre, les langages fournissent des options intéressantes pour les paradigmes de programmation orientée objet et fonctionnelle.

Ces langages offrent une grande diversité, en termes de philosophie et de syntaxe, mais également de symétrie fournie par un système de type partagé. Ce système de type est fourni par l’environnement d’exécution sous-jacent. .NET a été conçu autour de l’idée d’un « Common Language Runtime » pouvant prendre en charge les spécifications de langages divers, par exemple, les langages dynamiques et typés statiquement, et permettre une interopérabilité entre eux. Par exemple, vous pouvez passer une collection d’objets `People` entre les langages sans perte de capacité ou de sémantique.

Plusieurs [implémentations et produits .NET](components.md) sont disponibles, basés sur des [normes .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) ouvertes qui spécifient les principes fondamentaux de la plateforme. Ils sont optimisés en fonction des types différents d’application (par exemple, bureau, mobile, jeu, cloud) et prennent en charge plusieurs processeurs (par exemple, x86/x64, ARM) et systèmes d’exploitation (par exemple, Windows, Linux, iOS, Android, macOS). L’open source est également une partie importante de l’écosystème .NET, avec plusieurs implémentations .NET et de nombreuses bibliothèques disponibles sous licences certifiées OSI.

- En savoir plus sur [C#](../csharp/index.md)
- En savoir plus sur [F#](../fsharp/index.md)
- Parcourir la [bibliothèque des API .NET](../../api/index.md)
- [Présentation du Common Language Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/intro-to-clr.md)

<a name="fundamentals"></a>Notions de base
------------

**Multilingue** -.NET fournit un système de type bien défini, des formats de fichiers, un runtime, un framework et des outils qui peuvent être utilisés par plusieurs langages, à la fois pour leur propre exécution et pour interagir avec d’autres langages utilisant les mêmes composants de .NET comme devise partagée.

**Gestion de la mémoire** -.NET gère automatiquement la mémoire pour vous par le biais du garbage collector. Il s’assure que vous référencez systématiquement des objets actifs, vous évitant des problèmes désagréables tels que les dépassements de mémoire tampon et les violations d’accès. Cela inclut la vérification des limites d’index de tableau.

**Sécurité de type** - Les « types » constituent le principal modèle .NET pour les fonctionnalités et la représentation en mémoire. Les types définissent la forme et éventuellement le comportement. Grâce au runtime, le code appelant ne peut agir que sur les types en fonction de leur définition et de la visibilité spécifiée des membres, fournissant des résultats cohérents, fiables et sécurisés.

<a name="features"></a>Fonctionnalités
--------

**Types valeur définis par l’utilisateur** - Les types valeur sont une catégorie de types utile, car ils offrent la sémantique « passage par valeur » au lieu de « passage par référence », comme c’est le cas pour les classes. Les types valeur conviennent tout particulièrement pour les données numériques. .NET autorise les types valeur pour les types primitifs, tels que des entiers, et les types définis par l’utilisateur.

**Types génériques** - Les types génériques sont des types avec un ou plusieurs paramètres de type qui peuvent être spécifiés instanciation par instanciation. Cela est utile pour de nombreux types, qui sinon exposeraient du contenu comme le type Object ou nécessiteraient plusieurs définitions de type. Par exemple, une instanciation spécifique d’un type de collection peut devenir spécifique à des personnes, à des emplacements GPS ou à des chaînes.

**Réflexion** - .NET définit un format de métadonnées qui décrit les types dans un binaire. Le sous-système de réflexion utilise ces données, exposant les API pour la lecture et l’instanciation des types au moment de l’exécution. Cette fonctionnalité est très utile pour les scénarios dynamiques où il n’est pas pratique de connaître à l’avance l’implémentation exacte d’un programme.

**Génération de code flexible** - .NET n’impose pas une approche spécifique de la transformation des binaires .NET en code machine. Plusieurs approches ont été utilisées avec succès, notamment l’interprétation, la compilation juste-à-temps (JIT), la compilation Ahead Of Time (AOT) avec secours JIT et la compilation AOT sans secours JIT. Chacune de ces stratégies peut être précieuse, et il existe des opportunités pour leur utilisation conjointe.

**Multiplateforme** -.NET a été conçu pour être multiplateforme dès le départ. Le format binaire et le jeu d’instructions sont indépendants du système d’exploitation, du processeur et de la taille du pointeur. Un binaire .NET généré en 2000 pour être exécuté sur un ordinateur Windows 32 bits peut s’exécuter sur un appareil iOS ARM64 en 2016 sans subir de modification.

<a name="open-source"></a>Ouvrir la source
-----------

Les implémentations [.NET Core](https://github.com/dotnet/core) et [Mono](https://github.com/mono/mono) de .NET sont open source, sous licence MIT. La documentation utilise la licence [Creative Commons CC-BY](https://creativecommons.org/licenses/by/4.0/). .NET Core et Mono sont soutenus par Microsoft et ont de nombreux collaborateurs au sein de la communauté. 

Ces runtimes généralistes peuvent servir de base pour la recherche universitaire ou des produits d’apprentissage/formation ou commerciaux. Leur nature ouverte signifie également que tout le monde peut contribuer au code produit en amont, sur la base d’un bogue ou du désir d’une nouvelle fonctionnalité.

<a name="projects"></a>Projets
--------

- [CoreCLR](https://github.com/dotnet/coreclr) - Runtime .NET, utilisé par .NET Core.
- [Mono](https://github.com/mono/mono) - Runtime .NET, utilisée par Xamarin, entre autres.
- [CoreFX](https://github.com/dotnet/coreclr) - Bibliothèques de classes .NET, utilisées par .NET Core et, dans une certaine mesure, par Mono par le biais du partage de code source.
- [Roslyn](https://github.com/dotnet/roslyn) - Compilateurs C# et Visual Basic, utilisés par la plupart des outils et des plateformes .NET. Expose les API de lecture, d’écriture et d’analyse du code source.
- [F#](https://github.com/microsoft/visualfsharp) - Compilateur F#.
- [SDK Xamarin](http://open.xamarin.com) - Outils et bibliothèques nécessaires pour écrire des applications Android, iOS et macOS en C# et F#.

<a name="standardized"></a>Standardisé
------------

.NET est spécifié par le biais de [normes ECMA](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) ouvertes qui décrivent ses fonctionnalités et qui peuvent servir à effectuer une nouvelle implémentation. Il existe d’autres implémentations .NET, Mono et Unity étant les plus populaires au-delà de celles de Microsoft.


