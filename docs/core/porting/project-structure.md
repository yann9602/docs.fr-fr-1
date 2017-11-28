---
title: Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core
description: "Aide destinée aux propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core."
keywords: .NET, .NET Core, .NET Framework, disposition du projet, plusieurs frameworks
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.openlocfilehash: 93bec65e3bbee93855d6f5bce5e2d6cea8bb9f3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core

Cet article vise à aider les propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core. Il fournit plusieurs options pour organiser les projets de façon à aider les développeurs à atteindre cet objectif. La liste suivante fournit quelques scénarios classiques à prendre en compte quand vous devez décider comment configurer la disposition de votre projet avec .NET Core. La liste peut ne pas couvrir tout ce que vous souhaitez : établissez vos priorités en fonction des besoins de votre projet.

* [**Combiner des projets existants et des projets .NET Core en projets uniques**][option-csproj]

  *En voici les avantages :*
  * Simplification de votre processus de génération : compilation d’un seul projet au lieu de plusieurs, chacun ciblant une version du .NET Framework ou une plateforme différente.
  * Simplification de la gestion des fichiers sources pour les projets multiciblés car vous devez gérez un seul fichier projet. Lors de l’ajout/suppression de fichiers sources, les alternatives vous obligent à synchroniser manuellement ces fichiers avec vos autres projets.
  * Génération facile d’un package NuGet à consommer.
  * Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.

  *Scénarios non pris en charge :*
  * Demander aux développeurs d’utiliser Visual Studio 2017 pour ouvrir des projets existants. Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.

* <a name="support-vs"></a>[**Séparer les projets existants des nouveaux projets .NET Core**][option-csproj-folder]

  *En voici les avantages :*
  * Continuation de la prise en charge du développement de projets existants sans devoir mettre à niveau pour les développeurs/contributeurs qui n’ont pas Visual Studio 2017.
  * Réduction du risque de création de bogues dans des projets existants car aucune évolution du code n’est nécessaire dans ces projets.

## <a name="example"></a>Exemple

Considérez le dépôt ci-dessous :

![Projet existant][example-initial-project]

[**Code source**][example-initial-project-code]

La section suivante décrit plusieurs méthodes pour ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Remplacer les projets existants par un projet .NET Core multiciblé

Réorganisez le dépôt de sorte que tous les fichiers *\*.csproj* existants soient supprimés et qu’un seul fichier *\*.csproj* ciblant plusieurs frameworks soit créé. Il s’agit d’une option intéressante car un même projet peut être compilé pour différents frameworks. Elle permet également de gérer différentes options de compilation et dépendances par framework ciblé.

![Créer un csproj ciblant plusieurs frameworks][example-csproj]

[**Code source**][example-csproj-code]

Les modifications à noter sont :
* Remplacement de *packages.config* et de *\*.csproj* par un nouveau [.csproj *\*.NET Core*][example-csproj-netcore]. Les packages NuGet sont spécifiés avec `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Conserver les projets existants et créer un projet .NET Core

Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.

![Projet .NET Core avec un projet existant dans un dossier différent][example-csproj-different-folder]

[**Code source**][example-csproj-different-code]

Les modifications à noter sont :
* Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts.
    * Le fait de conserver les projets dans des dossiers distincts vous évite de devoir installer Visual Studio 2017. Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.

## <a name="see-also"></a>Voir aussi

Consultez la [documentation relative au portage vers .NET Core][porting-doc] pour obtenir de l’aide sur la migration vers .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projet existant"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Créer un csproj ciblant plusieurs frameworks"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projet .NET Core avec une bibliothèque de classes portable dans un dossier différent"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
