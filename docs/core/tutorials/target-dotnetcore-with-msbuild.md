---
title: "Création de projets .NET Core à l’aide de MSBuild"
description: "Création de projets .NET Core à l’aide de MSBuild"
keywords: .NET, .NET Core
author: dsplaisted
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13c66464-4f14-4db6-aa8b-06f25e7ba894
translationtype: Human Translation
ms.sourcegitcommit: 098cb31bb79e47ebb2ad2e8c2f56d2d5d6da4079
ms.openlocfilehash: 6a992d985948a22da58db8317bc04d2f1828fc05
ms.lasthandoff: 01/18/2017

---

# <a name="using-msbuild-to-build-net-core-projects"></a>Création de projets .NET Core à l’aide de MSBuild

Les outils .NET Core vont [passer de projets basés sur project.json à des projets basés sur MSBuild](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/).
Nous prévoyons de fournir la première version des outils .NET Core utilisant MSBuild lors de la prochaine version de Visual Studio.  Toutefois, il est d’ores et déjà possible d’utiliser MSBuild pour les projets .NET Core. Cette page montre comment procéder.

Nous vous recommandons d’utiliser les outils par défaut avec *project.json* pour les nouveaux projets ciblant .NET Core, et ce pour les raisons suivantes :

- MSBuild ne prend pas encore en charge un grand nombre des fonctionnalités de *project.json*.
- De nombreux outils basés sur ASP.NET ne fonctionnent pas encore avec les projets MSBuild.
- Lorsque des outils .NET Core basés sur MSBuild sont publiés, ils sont automatiquement convertis de *project.json* vers MSBuild.

Envisagez d’utiliser MSBuild pour :

 - Les projets existants qui utilisent MSBuild et sont portés vers .NET Core.
 - Les projets qui utilisent l’extensibilité de MSBuild et ne sont pas bien pris en charge par *project.json*.

## <a name="prerequisites"></a>Conditions préalables

- [Visual Studio 2015 Update 3](https://www.visualstudio.com/en-us/news/releasenotes/vs2015-update3-vs) ou version ultérieure
- [Outils .NET Core pour Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs)
- Extension Visual Studio NuGet [v3.5.0 bêta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou version ultérieure

## <a name="creating-a-library-targeting-net-core"></a>Création d’une bibliothèque ciblant .NET Core

1. Dans la barre de menus Visual Studio, choisissez **Fichier** | **Nouveau** | **Projet**, puis sélectionnez **Bibliothèque de classes (Portable)**

  ![Nouveau projet](./media/target-dotnetcore-with-msbuild/new-project-dialog-class-library-portable.png)

2. Choisissez un nom et un emplacement pour votre projet, puis cliquez sur **OK**

3. La boîte de dialogue « Ajouter la bibliothèque de classes portables » s’affiche.  Sélectionnez **.NET Framework 4.6** et **ASP.NET Core 1.0** comme cibles, puis cliquez sur **OK**

  ![Boîte de dialogue des cibles portables](./media/target-dotnetcore-with-msbuild/pcl-targets-dialog-net46-aspnetcore10.png)

4. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis choisissez **Propriétés**
5. Sous l’onglet **Bibliothèque** des propriétés du projet, cliquez sur le lien **Cibler .NET Platform Standard**, puis cliquez sur **Oui** dans la boîte de dialogue qui s’affiche
6. Ouvrez le fichier `project.json` dans votre projet, puis apportez les modifications suivantes :
    - Remplacez le numéro de version du package `NETStandard.Library` par `1.6.0` (il s’agit de la version .NET Core 1.0 du package)
    - Ajoutez la définition `imports` ci-dessous à l’intérieur de la définition du framework `netstandard1.6`.  Cette opération permet à votre projet de référencer des packages NuGet compatibles .NET Core qui n’ont pas été mis à jour pour cibler .NET Standard

        ```json
        "netstandard1.6": {
            "imports": [ "dnxcore50", "portable-net452" ]
        }
        ```

## <a name="creating-a-net-core-console-application"></a>Création d’une application console .NET Core
La création d’une application console pour .NET Core nécessite de personnaliser le processus de génération MSBuild.  Un exemple de projet pour une application console .NET Core appelée [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) est disponible dans le dépôt [corefxlab](https://github.com/dotnet/corefxlab).  Commencer avec [coretemplate](https://github.com/mellinoe/coretemplate), qui utilise des fichiers cibles MSBuild distincts pour cibler .NET Core, au lieu de placer les modifications directement dans le fichier projet constitue une autre bonne option.  

Il est également possible de commencer par créer un projet dans Visual Studio, puis de le modifier pour cibler .NET Core.  Les instructions ci-dessous indiquent les étapes de base pour que cela fonctionne correctement.  Contrairement à [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) ou [coretemplate](https://github.com/mellinoe/coretemplate), un projet créé de cette manière n’inclut pas de configurations pour cibler Linux et macOS.

1. Dans la barre de menus Visual Studio, choisissez **Fichier** | **Nouveau** | **Projet**, puis sélectionnez **Application console**
2. Choisissez un nom et un emplacement pour votre projet, puis cliquez sur **OK**
3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet, choisissez **Propriétés**, puis accédez à l’onglet **Générer**
4. Dans la liste déroulante **Configuration** (en haut de la page de propriétés), sélectionnez **Toutes les configurations**, puis remplacez la valeur **Plateforme cible** par **x64**
5. Supprimez le fichier `app.config`du projet
6. Ajoutez un fichier `project.json` au projet avec le contenu suivant :

    ```json
    {
        "dependencies": {
            "Microsoft.NETCore.App": "1.0.0-rc2-3002702"
        },
        "runtimes": {
            "win7-x64": { },
            "ubuntu.14.04-x64": { },
            "osx.10.10-x64": { }
        },
        "frameworks": {
            "netcoreapp1.0": {
                "imports": [ "dnxcore50", "portable-net452" ]
            }
        }
    }
    ```

7. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, choisissez **Décharger le projet**, recliquez avec le bouton droit, choisissez **Modifier _MyProj.csproj_**, puis apportez les modifications suivantes
    - Supprimez touts les éléments `Reference` par défaut (pour `System`, `System.Core`, etc.)
    - Ajoutez les propriétés suivantes au premier `PropertyGroup` du projet :

        ```xml
        <TargetFrameworkIdentifier>.NETCoreApp</TargetFrameworkIdentifier>
        <TargetFrameworkVersion>v1.0</TargetFrameworkVersion>
        <BaseNuGetRuntimeIdentifier>win7</BaseNuGetRuntimeIdentifier>
        <NoStdLib>true</NoStdLib>
        <NoWarn>$(NoWarn);1701</NoWarn>
        ```

    - Ajoutez le code suivant à la fin du fichier (après l’importation de `Microsoft.CSharp.Targets`) :

        ```xml
        <PropertyGroup>
            <!-- We don't use any of MSBuild's resolution logic for resolving the framework, so just set these two
                    properties to any folder that exists to skip the GetReferenceAssemblyPaths task (not target) and
                    to prevent it from outputting a warning (MSB3644).
                -->
            <_TargetFrameworkDirectories>$(MSBuildThisFileDirectory)</_TargetFrameworkDirectories>
            <_FullFrameworkReferenceAssemblyPaths>$(MSBuildThisFileDirectory)</_FullFrameworkReferenceAssemblyPaths>

            <!-- MSBuild thinks all EXEs need binding redirects, not so for CoreCLR! -->
            <AutoUnifyAssemblyReferences>true</AutoUnifyAssemblyReferences>
            <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>

            <!-- Set up debug options to run with host, and to use the CoreCLR debug engine -->
            <StartAction>Program</StartAction>
            <StartProgram>$(TargetDir)dotnet.exe</StartProgram>
            <StartArguments>$(TargetPath)</StartArguments>
            <DebugEngines>{2E36F1D4-B23C-435D-AB41-18E608940038}</DebugEngines>
        </PropertyGroup>
        ```

    - Fermez le fichier .csproj, puis rechargez le projet dans Visual Studio

8. Vous êtes normalement en mesure d’exécuter votre programme avec la touche F5 dans Visual Studio ou à partir de la ligne de commande dans le dossier de sortie avec`dotnet MyApp.exe` 

