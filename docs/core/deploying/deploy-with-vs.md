---
title: "Déploiement d’applications .NET Core avec Visual Studio"
description: "Découvrir comment déployer des applications .NET Core avec Visual Studio"
keywords: ".NET, .NET Core, Déploiement .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5cc9de1371ba90532e20c11c9f82002ad5a5fa92
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="deploying-net-core-apps-with-visual-studio"></a>Déploiement d’applications .NET Core avec Visual Studio

Pour déployer une application .NET Core, vous pouvez soit effectuer un *déploiement dépendant du framework* (qui inclut vos binaires d’application, mais qui dépend de la présence de .NET Core sur le système cible), soit effectuer un *déploiement autonome* (qui inclut votre application et les binaires .NET Core). Pour obtenir une vue d’ensemble du déploiement des applications .NET Core, consultez [Déploiement d’applications .NET Core](index.md).

Les sections suivantes montrent comment utiliser Microsoft Visual Studio pour créer les genres de déploiements suivants :

- Déploiement dépendant du framework
- Déploiement dépendant du framework avec des dépendances tierces
- Déploiement autonome
- Déploiement autonome avec des dépendances tierces

Pour plus d’informations sur l’utilisation de Visual Studio pour développer des applications .NET Core, consultez [Prérequis pour .NET Core sur Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Déploiement dépendant du framework

Le déploiement d’un déploiement dépendant du framework sans dépendances tierces implique simplement la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus.  

1. créer le projet ;

   Sélectionnez **Fichier** > **Nouveau** > **Projet**. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **.NET Core** dans le volet des types de projets **Installé**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central. Entrez un nom de projet, tel que « FDD », dans la zone de texte **Nom**. Sélectionnez le bouton **OK**.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* dans l’éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Créez une build Debug de votre application.

   Sélectionnez **Générer** > **Générer la solution**. Vous pouvez également compiler et exécuter la build Debug de votre application en sélectionnant **Déboguer** > **Démarrer le débogage**.

1. Déployez votre application.

   Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application. Pour publier à partir de Visual Studio, effectuez les étapes suivantes :

      1. Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.

      1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.

      1. Sous l’onglet **Publier**, sélectionnez **Publier**. Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.

      1. L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**. Les paramètres de configuration du profil sont affichés dans la section **Résumé** de l’onglet.

   Les fichiers résultants sont placés dans un répertoire nommé `PublishOutput` qui se trouve dans un sous-répertoire du sous-répertoire *.\bin\release* de votre projet.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Déployez l’ensemble complet des fichiers d’application de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix. Une fois l’installation terminée, les utilisateurs peuvent exécuter votre application en utilisant la commande `dotnet` suivie du nom de l’application. Par exemple : `dotnet fdd.dll`.

Outre les binaires de l’application, votre programme d’installation doit également regrouper le programme d’installation du framework partagé ou vérifier qu’il est bien installé comme prérequis de l’installation de l’application.  L’installation du framework partagé nécessite un accès Administrateur/root car il est à l’échelle de la machine.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Déploiement dépendant du framework avec des dépendances tierces

Pour exécuter un déploiement dépendant du framework avec une ou plusieurs dépendances tierces, ces dépendances doivent être accessibles à votre projet. Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :

1. Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système. Pour ouvrir le Gestionnaire de package, sélectionnez **Outils** > **Gestionnaire de package NuGet** > **Gérer les packages NuGet pour la solution**.

1. Confirmez que `Newtonsoft.Json` est installé sur votre système et, si ce n’est pas le cas, installez-le. L’onglet **Installé** répertorie les packages NuGet installés sur votre système. Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche. Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.

1. Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet. Pour cela, sélectionnez votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.

Notez qu’un déploiement dépendant du framework avec des dépendances tierces n’est portable que dans la mesure de la portabilité de ses dépendances tierces. Par exemple, si une bibliothèque tierce prend uniquement en charge macOS, l’application n’est pas portable sur des systèmes Windows. Cela se produit si la dépendance tierce elle-même dépend du code natif. Un [serveur Kestrel](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) constitue un bon exemple, car il nécessite une dépendance native à [libuv](https://github.com/libuv/libuv). Quand un déploiement dépendant du framework est créé pour une application avec ce type de dépendance tierce, le résultat publié contient un dossier pour chaque [identificateur de runtime](../rid-catalog.md#what-are-rids) pris en charge par la dépendance native (et qui existe dans le package NuGet).

## <a name="simpleSelf"></a> Déploiement autonome sans dépendances tierces

L’exécution d’un déploiement autonome sans aucune dépendance tierce implique la création du projet, la modification du fichier *csproj*, la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus. 

1. créer le projet ;

   Sélectionnez **Fichier** > **Nouveau** > **Projet**. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez **.NET Core** dans le volet des types de projets **Installé**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central. Entrez un nom de projet, tel que « SCD », dans la zone de texte **Nom**, puis sélectionnez le bouton **OK**.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* dans votre éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Définissez les plateformes ciblées par votre application.

   1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Modifier SCD.csproj**.

   1. Créez une balise `<RuntimeIdentifiers>` dans la section `<PropertyGroup>` de votre fichier *csproj* qui définit les plateformes ciblées par votre application, et spécifiez l’identificateur de runtime de chaque plateforme ciblée. Notez que vous devez également ajouter un point-virgule pour séparer les identificateurs de runtime. Consultez [Catalogue des identificateurs de runtime](../rid-catalog.md) pour obtenir une liste des identificateurs de runtime. 

   Dans l’exemple suivant, l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.11.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   Notez que l’élément `<RuntimeIdentifiers>` peut être placé dans n’importe quelle section `<PropertyGroup>` de votre fichier *csproj*. Un exemple complet de fichier *csproj* figure plus loin dans cette section.

1. Créez une build Debug de votre application.

   Sélectionnez **Générer** > **Générer la solution**. Vous pouvez également compiler et exécuter la build Debug de votre application en sélectionnant **Déboguer** > **Démarrer le débogage**.

1. Publiez votre application.

   Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.

   Pour publier votre application à partir de Visual Studio, effectuez les étapes suivantes :

      1. Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.

      1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**. 

      1. Sous l’onglet **Publier**, sélectionnez **Publier**. Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.

      1. L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**. Les paramètres de configuration du profil sont affichés dans la section **Résumé** de l’onglet. **Runtime cible** identifie le runtime qui a été publié, et **Emplacement cible** l’endroit où les fichiers du déploiement autonome ont été écrits.

      1. Par défaut, Visual Studio écrit tous les fichiers publiés dans un répertoire unique. Pour des raisons pratiques, il est préférable de créer des profils séparés pour chaque runtime cible et de placer les fichiers publiés dans un répertoire spécifique à la plateforme. Vous devez donc créer un profil de publication distinct pour chaque plateforme cible. À présent, effectuez les étapes suivantes pour regénérer l’application pour chaque plateforme :

         1. Sélectionnez **Créer un profil** dans la boîte de dialogue **Publier**.

         1. Dans la boîte de dialogue **Choisir une cible de publication** remplacez l’emplacement indiqué dans **Choisir un dossier** par *bin\Release\PublishOutput\win10-x64*. Sélectionnez **OK**.

         1. Sélectionnez le nouveau profil (**FolderProfile1**) dans la liste des profils et vérifiez que le **Runtime cible** est `win10-x64`. Si ce n’est pas le cas, sélectionnez **Paramètres**. Dans la boîte de dialogue **Paramètres du profil**, définissez **Runtime cible** avec la valeur `win10-x64` et sélectionnez **Enregistrer**. Sinon, sélectionnez **Annuler**.

         1. Sélectionnez **Publier** pour publier votre application pour des plateformes Windows 10 64 bits.

         1. Suivez les étapes précédentes pour créer un profil pour la plateforme `osx.10.11-x64`. L’**Emplacement cible** est *bin\Release\PublishOutput\osx.10.11-x64* et le **Runtime cible** est `osx.10.11-x64`. Le nom attribué par Visual Studio à ce profil est **FolderProfile2**.

      Notez que chaque emplacement cible contient l’ensemble complet des fichiers nécessaires pour lancer votre application, à savoir les fichiers de votre application et tous les fichiers .NET Core.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.

Voici le fichier *csproj* complet pour ce projet.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Déploiement autonome avec des dépendances tierces

L’exécution d’un déploiement autonome avec une ou plusieurs dépendances tierces implique l’ajout des dépendances. Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :

1. Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système. Pour ouvrir le Gestionnaire de package, sélectionnez **Outils** > **Gestionnaire de package NuGet** > **Gérer les packages NuGet pour la solution**.

1. Confirmez que `Newtonsoft.Json` est installé sur votre système et, si ce n’est pas le cas, installez-le. L’onglet **Installé** répertorie les packages NuGet installés sur votre système. Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche. Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.

1. Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet en sélectionnant votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.

Voici le fichier *csproj* complet pour ce projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Quand vous déployez votre application, toutes les dépendances tierces utilisées dans votre application sont également incluses avec vos fichiers d’application. Il n’est pas nécessaire que les bibliothèques tierces soient déjà présentes sur le système sur lequel l’application s’exécute.

Notez que vous pouvez déployer un déploiement autonome avec une bibliothèque tierce seulement sur des plateformes prises en charge par cette bibliothèque. Cela revient à avoir des dépendances tierces avec des dépendances natives dans votre déploiement dépendant du framework, où les dépendances natives n’existent pas sur la plateforme cible, sauf si elles y ont été installées précédemment.

# <a name="see-also"></a>Voir aussi
[Déploiement d’applications .NET Core](index.md)   
[Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)   

