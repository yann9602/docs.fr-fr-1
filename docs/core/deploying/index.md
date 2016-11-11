---
title: "Déploiement d’applications .NET Core"
description: "Déploiement d’applications .NET Core"
keywords: ".NET, .NET Core, Déploiement .NET Core"
author: rpetrusha
manager: wpickett
ms.date: 09/08/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
translationtype: Human Translation
ms.sourcegitcommit: 663f4102b82512e64ab39d8046c7298a7cf37de7
ms.openlocfilehash: 96eb2cc7ca948b3e372fa1363b1741624d791d27

---

# <a name="net-core-application-deployment"></a>Déploiement d’applications .NET Core #

Vous pouvez créer deux types de déploiement pour les applications .NET Core : 

- Déploiement dépendant du framework. Comme son nom l’indique, un déploiement dépendant du framework s’appuie sur la présence d’une version partagée à l’échelle du système de .NET Core sur le système cible. Comme .NET Core est déjà présent, votre application est également portable entre des installations de .NET Core. Votre application contient seulement son propre code et les dépendances tierces qui sont en dehors des bibliothèques .NET Core. Les déploiements dépendant du framework contiennent des fichiers .dll qui peuvent être lancés avec l’[utilitaire dotnet](../tools/dotnet.md) à partir de la ligne de commande. Par exemple, `dotnet app.dll` exécute une application nommée `app`.

- Déploiement autonome. Contrairement à un déploiement dépendant du framework, un déploiement autonome ne s’appuie sur la présence d’aucun composant partagé sur le système cible. Tous les composants, notamment les bibliothèques .NET Core et le runtime .NET Core, sont inclus avec l’application et sont isolées des autres applications .NET Core. Les déploiements autonomes incluent un fichier exécutable (comme `app.exe` sur les plateformes Windows pour une application nommée `app`), qui est une version renommée de l’hôte .NET Core spécifique à la plateforme, et un fichier .dll (comme `app.dll`), qui est l’application elle-même.

## <a name="frameworkdependent-deployments-fdd"></a>Déploiements dépendant du framework ##

Pour un déploiement dépendant du framework, vous déployez seulement votre application et les dépendances tierces. Vous ne devez pas déployer .NET Core car votre application utilise la version de .NET Core qui est présente sur le système cible. Il s’agit du modèle de déploiement par défaut pour les applications .NET Core.

### <a name="why-create-a-frameworkdependent-deployment"></a>Pourquoi créer un déploiement dépendant du framework ? ###

Un déploiement dépendant du framework présente plusieurs avantages :

- Vous n’avez pas à définir à l’avance les systèmes d’exploitation cible sur lesquels votre application .NET Core s’exécutera. Comme .NET Core utilise un format de fichier PE commun pour les fichiers exécutables et les bibliothèques quel que soit le système d’exploitation, .NET Core peuvent exécuter votre application quel que soit le système d’exploitation sous-jacent. Pour plus d’informations sur le format de fichier PE, consultez [Format de fichier d’assembly .NET](../../standard/assembly-format.md).

- Votre package de déploiement est de petite taille. Vous devez seulement déployer votre application et ses dépendances, et non pas .NET Core lui-même.

- Plusieurs applications utilisent la même installation de .NET Core, ce qui réduit l’utilisation de l’espace disque et de la mémoire sur les systèmes hôtes.

Il existe également quelques inconvénients :

- Votre application peut s’exécuter seulement si la version de .NET Core que vous ciblez, ou une version ultérieure, est déjà installée sur le système hôte.

- Il est possible que le runtime et les bibliothèques .NET Core changent sans que vous le sachiez dans les versions futures. Dans de rares cas, ceci peut changer le comportement de votre application.

### <a name="deploying-a-frameworkdependent-deployment"></a>Déploiement d’un déploiement dépendant du framework ###

Le déploiement d’un déploiement dépendant du framework sans dépendances tierces implique simplement la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus. L’exemple utilise l’[utilitaire dotnet](../tools/dotnet.md) à partir de la ligne de commande. Vous pouvez cependant utiliser aussi un environnement de développement, comme Visual Studio ou Visual Studio Code, pour compiler, tester et publier l’exemple.

1. Créez un répertoire pour votre projet et, à partir de la ligne de commande, tapez [dotnet new](../tools/dotnet-new.md) pour créer un nouveau projet de console C#.

2. Ouvrez le fichier `Program.cs` dans un éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte, puis affiche les différents mots entrés par l’utilisateur. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else
              {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. Exécutez la commande [dotnet restore](../tools/dotnet-restore.md) pour restaurer les dépendances spécifiées dans votre projet.

4. Créez une version Debug de votre application à l’aide de la commande [dotnet build](../tools/dotnet-build.md).

5. Une fois que vous avez débogué et testé le programme, vous pouvez créer les fichiers à déployer avec votre application à l’aide de la commande `dotnet publish -f netcoreapp1.0 -c release`. Ceci crée une version de publication (au lieu d’une version debug) de votre application.

   Les fichiers résultants sont placés dans un répertoire nommé `publish` qui se trouve dans un sous-répertoire du sous-répertoire `.\bin\release\netcoreapp1.0` de votre projet.

6. En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est utile principalement pour le débogage des exceptions ; vous pouvez choisir de ne pas le placer dans le package avec les fichiers de votre application.

L’ensemble complet des fichiers de l’application peut être déployé de la façon que vous préférez. Par exemple, vous pouvez les packager dans un fichier zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.

Outre les fichiers binaires d’application, le programme d’installation doit également regrouper le programme d’installation du framework partagé ou vérifier qu’il est bien installé comme prérequis de l’installation de l’application.  L’installation du framework partagé nécessite un accès Administrateur/root car il est à l’échelle de la machine.

### <a name="deploying-a-frameworkdependent-deployment-with-thirdparty-dependencies"></a>Déploiement d’un déploiement dépendant du framework avec des dépendances tierces ###

Déployer un déploiement dépendant du framework avec une ou plusieurs dépendances tierces implique trois étapes supplémentaires avant de pouvoir exécuter la commande `dotnet restore` :

1. Ajouter des références à des bibliothèques tierces à la section `dependencies` de votre fichier `project.json`. La section `dependencies` suivante utilise Json.NET comme bibliothèque tierce.

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": {
        "type": "platform",
        "version": "1.0.0"
      },
      "Newtonsoft.Json": "9.0.1"
    },
    ```

2. Si vous ne l’avez pas encore fait, téléchargez le package NuGet contenant les dépendances tierces. Pour télécharger le package, exécutez la commande `dotnet restore` après avoir ajouté la dépendance. Comme la dépendance est résolue à partir du cache NuGet local au moment de la publication, elle doit être disponible sur votre système.

Notez qu’un déploiement dépendant du framework avec des dépendances tierces n’est portable que dans la mesure de la portabilité de ses dépendances tierces. Par exemple, si une bibliothèque tierce prend en charge seulement macOS, l’application n’est pas portable sur des systèmes Windows. Ce cas peut se produire si la dépendance tierce elle-même dépend d’un code natif. Le serveur Kestrel en est un bon exemple. Quand un déploiement dépendant du framework est créé pour une application avec ce type de dépendance tierce, le résultat publié contient un dossier pour chaque [identificateur de runtime](../rid-catalog.md#what-are-rids) pris en charge par la dépendance native (et qui existe dans le package NuGet).

## <a name="selfcontained-deployments-scd"></a>Déploiements autonomes ##

Pour un déploiement autonome, vous déployez non seulement votre application et les dépendances tierces, mais aussi la version de .NET Core avec laquelle vous générez votre application. La création d’un déploiement autonome n’inclut cependant pas les [dépendances natives de .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) lui-même sur les différentes plateformes (par exemple OpenSSL sur macOS). Ces services doivent donc être installés avant d’exécuter l’application. 

### <a name="why-deploy-a-selfcontained-deployment"></a>Pourquoi déployer un déploiement autonome ? ###

Le déploiement d’un déploiement autonome a deux avantages majeurs :

- Vous avez le contrôle exclusif de la version de .NET Core qui est déployée avec votre application. Vous pouvez vous-même assurer toute la maintenance de .NET Core.

- Vous avez la garantie que le système cible peut exécuter votre application .NET Core puisque vous fournissez la version du .NET Core sur laquelle elle est exécutée.

Elle a également plusieurs inconvénients :

- Comme .NET Core est inclus dans votre package de déploiement, vous devez choisir à l’avance les plateformes cibles pour lesquels vous générez des packages de déploiement.

- La taille de votre package de déploiement est relativement importante car vous devez inclure .NET Core ainsi que votre application et ses dépendances tierces.

- Le déploiement de nombreuses applications .NET Core autonomes sur un système peut consommer une quantité significative d’espace disque car chaque application duplique les fichiers de .NET Core.

### <a name="a-namesimpleselfa-deploying-a-simple-selfcontained-deployment"></a> Déploiement d’un déploiement autonome simple ###

Le déploiement d’un déploiement autonome sans dépendances tierces implique la création du projet, la modification du fichier project.json, la génération, le test et la publication de l’application.  Un exemple simple écrit en C# illustre le processus. L’exemple utilise l’utilitaire `dotnet` à partir de la ligne de commande. Vous pouvez cependant utiliser aussi un environnement de développement, comme Visual Studio ou Visual Studio Code, pour compiler, tester et publier l’exemple.

1. Créez un répertoire pour votre projet et, à partir de la ligne de commande, tapez `dotnet new` pour créer un nouveau projet de console C#.

2. Ouvrez le fichier `Program.cs` dans un éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte, puis affiche les différents mots entrés par l’utilisateur. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. Ouvrez le fichier `project.json` et, dans la section `frameworks`, supprimez la ligne suivante :

   ```json
   "type": "platform",
   ```
La section Framework doit ressembler à ceci une fois que vous l’avez modifiée :

    ```json
    "frameworks": {
      "netcoreapp1.0": {
        "dependencies": {
          "Microsoft.NETCore.App": {
             "version": "1.0.0"
          }
        }
      }
    }
    ```
La suppression de l’attribut `"type": "platform"` indique que le framework est fourni comme un ensemble de composants locaux à notre application, au lieu d’un package de plateforme à l’échelle du système.

4. Créez une section `runtimes` dans votre fichier `project.json` qui définit les plateformes ciblées par votre application, et spécifiez l’identificateur de runtime de chaque plateforme que vous ciblez. Consultez [Catalogue des identificateurs de runtime](../rid-catalog.md) pour obtenir une liste des identificateurs de runtime. Par exemple, la section `runtimes` suivante indique que l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.10.

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
Notez que vous devez également ajouter une virgule pour séparer la section `runtimes` de la section précédente.
Un exemple complet de fichier `project.json` figure plus loin dans cette section.

6. Exécutez la commande `dotnet restore`pour restaurer les dépendances spécifiées dans votre projet.

7. Créez des versions debug de votre application sur chacune des plateformes cibles en utilisant la commande `dotnet build`. Sauf si vous spécifiez l’identificateur de runtime que vous voulez générer, la commande `dotnet build` crée une build seulement pour l’ID de runtime du système actif. Vous pouvez générer votre application pour les deux plateformes cibles avec les commandes :

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```
Les versions Debug de votre application pour chaque plateforme se trouvent dans le sous-répertoire `.\bin\Debug\netcoreapp1.0\<runtime_identifier>` du projet.

8. Une fois que vous avez débogué et testé le programme, vous pouvez créer les fichiers à déployer avec votre application pour chaque plateforme qu’elle cible en utilisant la commande `dotnet publish` pour les deux plates-formes comme suit :

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
Ceci crée une version de publication (au lieu d’une version debug) de votre application pour chaque plateforme cible. Les fichiers résultants sont placés dans un sous-répertoire nommé `publish` qui se trouve dans un sous-répertoire du sous-répertoire `.\bin\release\netcoreapp1.0\<runtime_identifier>` de votre projet. Notez que chaque sous-répertoire contient l’ensemble complet des fichiers (les fichiers de votre application et tous les fichiers .NET Core) nécessaires pour lancer votre application.

9. En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est utile principalement pour le débogage des exceptions ; vous pouvez choisir de ne pas le placer dans le package avec les fichiers de votre application.

Les fichiers publiés peuvent être déployés de la façon de votre choix. Par exemple, vous pouvez les packager dans un fichier zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix. 

Voici le fichier `project.json`complet pour ce projet.

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {},
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "version": "1.0.0"
        }
      }
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

### <a name="deploying-a-selfcontained-deployment-with-thirdparty-dependencies"></a>Déploiement d’un déploiement autonome avec des dépendances tierces ###

Le déploiement d’un déploiement autonome avec une ou plusieurs dépendances tierces implique l’ajout des dépendances tierces :

1. Ajouter des références à des bibliothèques tierces à la section `dependencies` de votre fichier `project.json`. La section `dependencies` suivante utilise Json.NET comme bibliothèque tierce.

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": "1.0.0",
      "Newtonsoft.Json": "9.0.1"
    },
    ```
2. Si vous ne l’avez pas encore fait, téléchargez le package NuGet contenant les dépendances tierces sur votre système. Pour rendre la dépendance disponible pour votre application, exécutez la commande `dotnet restore` après l’ajout de la dépendance. Comme la dépendance est résolue à partir du cache NuGet local au moment de la publication, elle doit être disponible sur votre système.

Voici le fichier project.json complet pour ce projet :

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0",
    "Newtonsoft.Json": "9.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

Quand vous déployez votre application, toutes les dépendances tierces utilisées dans votre application sont également incluses avec vos fichiers d’application. Il n’est pas nécessaire que les bibliothèques tierces soient déjà présentes sur le système sur lequel l’application s’exécute.

Notez que vous pouvez déployer un déploiement autonome avec une bibliothèque tierce seulement sur des plateformes prises en charge par cette bibliothèque. Ceci est similaire à avoir des dépendances tierces avec des dépendances natives dans votre déploiement dépendant du framework. 

### <a name="deploying-a-selfcontained-deployment-with-a-smaller-footprint"></a>Déploiement d’un déploiement autonome avec un encombrement réduit ###

Si la disponibilité de l’espace de stockage adéquat sur les systèmes cibles peut poser un problème, vous pouvez réduire l’encombrement global de votre application en excluant certains composants système. Pour cela, vous définissez explicitement les composants .NET Core que votre application inclut dans votre fichier project.json.

Pour créer un déploiement autonome avec un encombrement réduit, commencez par les deux premières étapes de création d’un déploiement autonome. Une fois que vous avez exécuté la commande `dotnet new` et ajouté le code source C# à votre application, procédez comme suit :

1. Ouvrez le fichier `project.json`et remplacez la section `frameworks` par ce qui suit :

    ```json
    "frameworks": {
      "netstandard1.6": { }
    }
    ```
Ceci fait deux choses :

    * Il indique que, au lieu d’utiliser la totalité du framework `netcoreapp1.0`, qui comprend .NET Core CLR, la bibliothèque .NET Core et plusieurs autres composants système, notre application utilise seulement la bibliothèque .NET Standard.

    * La suppression de l’attribut `"type": "platform"` indique que le framework est fourni comme un ensemble de composants locaux à notre application, au lieu d’un package de plateforme à l’échelle du système.

2. Remplacez la section `dependencies` par ce qui suit :

    ```json
    "dependencies": {
      "NETStandard.Library": "1.6.0",
      "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
      "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
    },
    ```
   Ceci définit les composants système utilisés par votre application. Les composants système packagés avec notre application incluent la bibliothèque .NET Standard, le runtime .NET Core et l’hôte .NET Core. Ceci produit un déploiement autonome avec un encombrement réduit.

3. Comme vous l’avez fait dans l’exemple [Déploiement d’un déploiement autonome simple](#simpleSelf), créez une section `runtimes` dans votre fichier `project.json` qui définit les plateformes ciblées par votre application, et spécifiez l’identificateur de runtime de chaque plateforme que vous ciblez. Consultez [Catalogue des identificateurs de runtime](../rid-catalog.md) pour obtenir une liste des identificateurs de runtime. Par exemple, la section `runtimes` suivante indique que l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.10.

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
Notez que vous devez également ajouter une virgule pour séparer la section `runtimes` de la section précédente.
Un exemple complet de fichier `project.json` figure plus loin dans cette section.

4. Exécutez la commande `dotnet restore`pour restaurer les dépendances spécifiées dans votre projet.

5. Créez des versions debug de votre application sur chacune des plateformes cibles en utilisant la commande `dotnet build`. Sauf si vous spécifiez l’identificateur de runtime que vous voulez générer, la commande `dotnet build` crée une build seulement pour l’ID de runtime du système actif. Vous pouvez générer votre application pour les deux plateformes cibles avec les commandes :

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```

6. Une fois que vous avez débogué et testé le programme, vous pouvez créer les fichiers à déployer avec votre application pour chaque plateforme qu’elle cible en utilisant la commande `dotnet publish` pour les deux plates-formes comme suit :

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
Ceci crée une version de publication (au lieu d’une version debug) de votre application pour chaque plateforme cible. Les fichiers résultants sont placés dans un sous-répertoire nommé `publish` qui se trouve dans un sous-répertoire du sous-répertoire `.\bin\release\netstandard1.6\<runtime_identifier>` de votre projet. Notez que chaque sous-répertoire contient l’ensemble complet des fichiers (les fichiers de votre application et tous les fichiers .NET Core) nécessaires pour lancer votre application.

7. En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est utile principalement pour le débogage des exceptions ; vous pouvez choisir de ne pas le placer dans le package avec les fichiers de votre application.

Les fichiers publiés peuvent être déployés de la façon de votre choix. Par exemple, vous pouvez les packager dans un fichier zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix. 

Voici le fichier `project.json`complet pour ce projet.

```json
   {
     "version": "1.0.0-*",
     "buildOptions": {
       "debugType": "portable",
       "emitEntryPoint": true
     },
     "dependencies": {
       "NETStandard.Library": "1.6.0",
       "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
       "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
     },
     "frameworks": {
       "netstandard1.6": { }
     },
     "runtimes": {
       "win10-x64": {},
       "osx.10.10-x64": {}
     }
   }
```



<!--HONumber=Nov16_HO1-->


