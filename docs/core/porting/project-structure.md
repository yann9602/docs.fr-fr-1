---
title: Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core
description: Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core
keywords: .NET, .NET Core
author: conniey
ms.author: mairaw
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
translationtype: Human Translation
ms.sourcegitcommit: 405bac1faa446687a4acdcf2d5536ee31f31f246
ms.openlocfilehash: b86693b1d6eed0ff5b8d1831e324354241f29806
ms.lasthandoff: 03/15/2017

---

# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core

> [!WARNING]
> Cette rubrique n’a pas encore été mise à jour vers la dernière version des outils.

Cet article est destiné à aider les propriétaires de projet qui veulent compiler leur solution côte à côte pour le .NET Framework et .NET Core.  Il fournit plusieurs options pour organiser les projets de façon à aider les développeurs à atteindre cet objectif.  Voici quelques scénarios classiques à prendre en compte quand vous devez décider comment configurer la disposition de votre projet avec .NET Core.  Ils peuvent ne pas couvrir tout ce que vous voulez : établissez vos priorités en fonction des besoins de votre projet.

* [**Combiner des projets existants et des projets .NET Core en projets uniques**][option-xproj]
  
  *En voici les avantages :*
  * Simplification de votre processus de génération : compilation d’un seul projet au lieu de plusieurs, chacun ciblant une version du .NET Framework ou une plateforme différente.
  * Simplification de la gestion des fichiers sources pour les projets multiciblés car vous ne gérez qu’un seul fichier projet.  Lors de l’ajout/suppression de fichiers sources, les alternatives vous obligent à synchroniser manuellement ces fichiers avec vos autres projets.
  * Génération facile d’un package NuGet à consommer.
  * Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.
  
  *Scénarios non pris en charge :*
  * Ne permet pas aux développeurs ne disposant pas de Visual Studio 2015 d’ouvrir des projets existants. Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.
  * Ne vous permet pas de partager votre bibliothèque .NET Core entre différents types de projets dans le même fichier solution. Pour prendre ceci en charge, la [création d’une bibliothèque de classes portable](#support-pcl) est une meilleure option.
  * Ne permet pas les modifications de génération ou de chargement de projet qui sont prises en charge par les tâches et les cibles MSBuild. Pour prendre ceci en charge, la [création d’une bibliothèque de classes portable](#support-pcl) est une meilleure option.

* <a name="support-vs"></a>[**Séparer les projets existants des nouveaux projets .NET Core**][option-xproj-folder]
  
  *En voici les avantages :*
  * Continuation de la prise en charge du développement de projets existants sans devoir mettre à niveau pour les développeurs/collaborateurs qui n’ont pas Visual Studio 2015.
  * Réduction du risque de création de bogues dans des projets existants car aucune évolution du code n’est nécessaire dans ces projets.

* <a name="support-pcl"></a>[**Conserver les projets existants et créer des bibliothèques de classes portables ciblant .NET Core**][option-pcl]

  *En voici les avantages :*
  * Références à vos bibliothèques .NET Core dans les projets pour ordinateurs et/ou web ciblant tout le .NET Framework dans la même solution.
  * Prise en charge des modifications dans le processus de génération ou de chargement des projets. Ces modifications peuvent être l’inclusion de tâches et de cibles MSBuild dans votre fichier `*.csproj`.

  *Scénarios non pris en charge :*
  * Ne vous permet pas d’écrire du code pour une version spécifique du .NET Framework car les [symboles de préprocesseur prédéfinis][how-to-multitarget] ne sont pas pris en charge.

## <a name="example"></a>Exemple

Considérez le dépôt ci-dessous :

![Projet existant][example-initial-project]

[**Code source**][example-initial-project-code]

Il existe différents moyens d’ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants : ils sont décrits ci-dessous.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project-xproj"></a>Remplacer les projets existants par un projet .NET Core multiciblé (xproj)

Le dépôt peut être réorganisé de sorte que tous les fichiers `*.csproj` existants soient supprimés et qu’un seul fichier `*.xproj` ciblant plusieurs frameworks soit créé.  Il s’agit d’une option intéressante car un même projet peut être compilé pour différents frameworks.  Elle a également la possibilité de gérer différentes options de compilation, différentes dépendances, etc., par framework ciblé.

![Créer un projet xproj ciblant plusieurs frameworks][example-xproj]

[**Code source**][example-xproj-code]

Les modifications à noter sont :
* Ajout de `global.json`
* Remplacement de `packages.config` et de `*.csproj` par `project.json` et `*.xproj`
* Modifications dans le fichier [project.json de l’exemple Car][example-xproj-projectjson] et de son [projet de test][example-xproj-projectjson-test] pour prendre en charge la génération pour le .NET Framework existant ainsi que pour les autres

## <a name="create-a-portable-class-library-pcl-to-target-net-core"></a>Créer une bibliothèque de classes portable pour cibler .NET Core

Si des projets existants contiennent des opérations ou des propriétés de génération complexes dans leur fichier `*.csproj`, il peut être plus facile de créer une bibliothèque de classes portable.

![][example-pcl]

[**Code source**][example-pcl-code]

Les modifications à noter sont :
*  Renommage de `project.json` en `{project-name}.project.json`
    * Ceci empêche un conflit potentiel dans Visual Studio quand vous tentez de restaurer des packages pour les bibliothèques dans le même répertoire. Pour plus d’informations, consultez le [Forum aux questions sur NuGet](https://docs.nuget.org/consume/nuget-faq#working-with-packages) sous « _I have multiple projects in the same folder, how can I use separate packages.config or project.json files for each project?_ ».
    *  **Alternative** : créer la bibliothèque de classes portable dans un autre dossier et faire référence au code source d’origine pour éviter ce problème.  Placer la bibliothèque de classes portable dans un autre dossier a cet avantage supplémentaire que les utilisateurs ne disposant pas de Visual Studio 2015 peuvent continuer à travailler sur les anciens projets sans charger la nouvelle solution.
*  Pour cibler .NET Standard après avoir créé la bibliothèque de classes portable, dans Visual Studio, ouvrez les **Propriétés du projet**. Sous la section **Cibles**, cliquez sur le lien **« Cibler .NET Platform Standard »**.  Cette modification peut être inversée en répétant la même procédure.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Conserver les projets existants et créer un projet .NET Core

Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.

![Projet .NET Core avec une bibliothèque de classes portable dans un dossier différent][example-xproj-different-folder]

[**Code source**][example-xproj-different-code]

Les modifications à noter sont :
* Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts.
    * Ceci évite le problème de restauration de package qui a été mentionné plus haut, dû au fait que plusieurs fichiers project.json/package.config se trouvent dans le même dossier.
    * Conserver les projets dans des dossiers distincts vous évite de devoir disposer de Visual Studio 2015 (en raison du fichier project.json).  Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.

## <a name="see-also"></a>Voir aussi

Consultez [Documentation du portage vers .NET Core][porting-doc] pour obtenir des instructions sur le passage à project.json et xproj.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projet existant"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-xproj]: media/project-structure/project.xproj.png "Créer un projet xproj ciblant plusieurs frameworks"
[example-xproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/
[example-xproj-projectjson]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/src/Car/project.json
[example-xproj-projectjson-test]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/tests/Car.Tests/project.json

[example-xproj-different-folder]: media/project-structure/project.xproj.different.png "Projet .NET Core avec une bibliothèque de classes portable dans un dossier différent"
[example-xproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj-keep-csproj/

[example-pcl]: media/project-structure/project.pcl.png "Bibliothèque de classes portable ciblant .NET Core"
[example-pcl-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-pcl

[option-xproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project-xproj
[option-pcl]: #create-a-portable-class-library-pcl-to-target-net-core
[option-xproj-folder]: #keep-existing-projects-and-create-a-net-core-project

[how-to-multitarget]: ../tutorials/libraries.md#how-to-multitarget

