---
title: "Déploiement d’applications .NET Core avec les outils CLI"
description: "Apprendre à déployer des applications .NET Core avec les outils de l’interface de ligne de commande (CLI)"
keywords: ".NET, .NET Core, Déploiement .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.openlocfilehash: fc7a40667c9b0a623bb0ebdf4ad60783fa58e6c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Déploiement d’applications .NET Core avec les outils de l’interface de ligne de commande (CLI)

Pour déployer une application .NET Core, vous pouvez soit effectuer un *déploiement dépendant du framework* (qui inclut vos binaires d’application, mais qui dépend de la présence de .NET Core sur le système cible), soit effectuer un *déploiement autonome* (qui inclut votre application et les binaires .NET Core). Pour obtenir une vue d’ensemble, consultez [Déploiement d’applications .NET Core](index.md).

Les sections suivantes montrent comment utiliser les [outils de l’interface de ligne de commande .NET Core](../tools/index.md) pour créer les genres de déploiements suivants :

- Déploiement dépendant du framework
- Déploiement dépendant du framework avec des dépendances tierces
- Déploiement autonome
- Déploiement autonome avec des dépendances tierces

Si vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’éditeur de programme de votre choix. Si vous utilisez [Visual Studio Code](https://code.visualstudio.com) comme éditeur de programme, vous pouvez ouvrir une console de commande dans votre environnement Visual Studio Code en sélectionnant **Afficher** > **Terminal intégré**.

## <a name="framework-dependent-deployment"></a>Déploiement dépendant du framework

Le déploiement d’un déploiement dépendant du framework sans dépendances tierces implique simplement la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus. 

1. Créez un répertoire de projet.

   Créez un répertoire pour votre projet et définissez-le comme répertoire actif.

1. créer le projet ;

   À partir de la ligne de commande, tapez [dotnet new console](../tools/dotnet-new.md) pour créer un projet de console C# dans ce répertoire.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* dans votre éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Mettez à jour les dépendances et les outils du projet.
 
   Exécutez le [dotnet restauration](../tools/dotnet-restore.md) ([voir la Remarque](#dotnet-restore-note)) pour restaurer les dépendances spécifiées dans votre projet.

1. Créez une build Debug de votre application.

   Utilisez la commande [dotnet build](../tools/dotnet-build.md) pour générer votre application ou [dotnet run](../tools/dotnet-run.md) pour générer et exécuter l’application.

1. Déployez votre application.

   Après avoir débogué et testé le programme, créez le déploiement à l’aide de la commande suivante :

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   Ceci crée une version de publication (au lieu d’une version Debug) de votre application. Les fichiers résultants sont placés dans un répertoire nommé *publish* qui se trouve dans un sous-répertoire du répertoire *bin* de votre projet.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas le distribuer avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Vous pouvez déployer l’ensemble complet des fichiers d’application de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix. Une fois l’installation terminée, les utilisateurs peuvent exécuter votre application en utilisant la commande `dotnet` suivie du nom de l’application. Par exemple : `dotnet fdd.dll`.

Outre les binaires de l’application, votre programme d’installation doit également regrouper le programme d’installation du framework partagé ou vérifier qu’il est bien installé comme prérequis de l’installation de l’application.  L’installation du framework partagé nécessite un accès Administrateur/racine.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Déploiement dépendant du framework avec des dépendances tierces

Pour exécuter un déploiement dépendant du framework avec une ou plusieurs dépendances tierces, ces dépendances doivent être accessibles à votre projet. Deux étapes supplémentaires sont nécessaires avant de pouvoir exécuter le `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) commande :

1. Ajoutez les références aux bibliothèques tierces exigées à la section `<ItemGroup>` de votre fichier *csproj*. La section `<ItemGroup>` suivante contient une dépendance à [Json.NET](http://www.newtonsoft.com/json) comme bibliothèque tierce :

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Si vous ne l’avez pas encore fait, téléchargez le package NuGet contenant les dépendances tierces. Pour télécharger le package, vous devez exécuter le `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) commande après l’ajout de la dépendance. Comme la dépendance est résolue à partir du cache NuGet local au moment de la publication, elle doit être disponible sur votre système.

Notez qu’un déploiement dépendant du framework avec des dépendances tierces n’est portable que dans la mesure de la portabilité de ses dépendances tierces. Par exemple, si une bibliothèque tierce prend uniquement en charge macOS, l’application n’est pas portable sur des systèmes Windows. Cela se produit si la dépendance tierce elle-même dépend du code natif. Un [serveur Kestrel](/aspnet/core/fundamentals/servers/kestrel) constitue un bon exemple, car il nécessite une dépendance native à [libuv](https://github.com/libuv/libuv). Quand un déploiement dépendant du framework est créé pour une application avec ce type de dépendance tierce, le résultat publié contient un dossier pour chaque [identificateur de runtime](../rid-catalog.md) pris en charge par la dépendance native (et qui existe dans le package NuGet).

## <a name="simpleSelf"></a> Déploiement autonome sans dépendances tierces

L’exécution d’un déploiement autonome sans dépendances tierces implique la création du projet, la modification du fichier *csproj*, la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus. L’exemple montre comment créer un déploiement autonome à l’aide de l’[utilitaire dotnet](../tools/dotnet.md) à partir de la ligne de commande.

1. Créez un répertoire pour le projet.

   Créez un répertoire pour votre projet et définissez-le comme répertoire actif.

1. créer le projet ;

   À partir de la ligne de commande, tapez [dotnet new console](../tools/dotnet-new.md) pour créer un projet de console C# dans ce répertoire.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* dans votre éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Définissez les plateformes ciblées par votre application.

   Créez une balise `<RuntimeIdentifiers>` dans la section `<PropertyGroup>` de votre fichier *csproj* qui définit les plateformes ciblées par votre application, puis spécifiez l’identificateur de runtime de chaque plateforme ciblée. Notez que vous devez également ajouter un point-virgule pour séparer les identificateurs de runtime. Consultez [Catalogue des identificateurs de runtime](../rid-catalog.md) pour obtenir une liste des identificateurs de runtime. 

   Par exemple, la section `<PropertyGroup>` suivante indique que l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.11.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Notez que l’élément `<RuntimeIdentifiers>` peut apparaître dans n’importe quelle section `<PropertyGroup>` de votre fichier *csproj*. Un exemple complet de fichier *csproj* figure plus loin dans cette section.

1. Mettez à jour les dépendances et les outils du projet.

   Exécutez le [dotnet restauration](../tools/dotnet-restore.md) ([voir la Remarque](#dotnet-restore-note)) pour restaurer les dépendances spécifiées dans votre projet.

1. Créez une build Debug de votre application.

   À partir de la ligne de commande, utilisez la commande [dotnet build](../tools/dotnet-build.md).

1. Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.

   Utilisez la commande `dotnet publish` pour les deux plateformes cibles comme suit :

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Ceci crée une version de publication (au lieu d’une version Debug) de votre application pour chaque plateforme cible. Les fichiers résultants sont placés dans un sous-répertoire nommé *publish* qui se trouve dans un sous-répertoire du sous-répertoire *.\bin\Release\netcoreapp1.1\<identificateur_runtime>* de votre projet. Notez que chaque sous-répertoire contient l’ensemble complet des fichiers (les fichiers de votre application et tous les fichiers .NET Core) nécessaires pour lancer votre application.

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

L’exécution d’un déploiement autonome avec une ou plusieurs dépendances tierces implique l’ajout des dépendances. Deux étapes supplémentaires sont nécessaires avant de pouvoir exécuter le `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) commande :

1. Ajoutez les références aux bibliothèques tierces à la section `<ItemGroup>` de votre fichier *csproj*. La section `<ItemGroup>` suivante utilise Json.NET comme bibliothèque tierce.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Si vous ne l’avez pas encore fait, téléchargez le package NuGet contenant les dépendances tierces sur votre système. Pour que la dépendance disponibles pour votre application, exécutez le `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) commande après l’ajout de la dépendance. Comme la dépendance est résolue à partir du cache NuGet local au moment de la publication, elle doit être disponible sur votre système.

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

Notez que vous pouvez déployer un déploiement autonome avec une bibliothèque tierce seulement sur des plateformes prises en charge par cette bibliothèque. Cela revient à avoir des dépendances tierces avec des dépendances natives dans un déploiement dépendant du framework, où les dépendances natives doivent être compatibles avec la plateforme sur laquelle l’application est déployée.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>Voir aussi

[Déploiement d’applications .NET Core](index.md)   
[Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)   

