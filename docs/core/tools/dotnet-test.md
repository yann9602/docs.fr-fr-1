---
title: Commande dotnet-test | SDK .NET Core
description: "La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné."
keywords: "dotnet-test, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: b12861f0ce3c40bf4db51994ea5d4a92b8ef0162

---

#<a name="dotnettest"></a>dotnet-test

## <a name="name"></a>Nom

`dotnet-test` : Exécute les tests unitaires à l’aide du Test Runner configuré

## <a name="synopsis"></a>Résumé

`dotnet test [project] [--help] 
    [--parentProcessId] [--port] [--configuration]   
    [--output] [--build-base-path] [--framework] [--runtime]
    [--no-build]`  

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. Les tests unitaires sont des projets de bibliothèques de classes qui ont des dépendances dans le framework de test unitaire (par exemple, NUnit ou xUnit) et dans le Test Runner dotnet de ce framework de test unitaire. Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.

Les projets de test doivent également spécifier une propriété Test Runner dans project.json en utilisant le nœud « testRunner ». Cette valeur doit contenir le nom du framework de test unitaire.

L’exemple de project.json suivant montre les propriétés nécessaires :

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {
    "System.Runtime.Serialization.Primitives": "4.1.1",
    "xunit": "2.1.0",
    "dotnet-test-xunit": "1.0.0-rc2-192208-24"
  },
  "testRunner": "xunit",
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.0.0"
        }
      },
      "imports": [
        "dotnet5.4",
        "portable-net451+win8"
      ]
    }
  }
}
```

`dotnet test` prend en charge deux modes d’exécution :

1. Console : en mode console, `dotnet test` exécute entièrement toutes les commandes qu’il reçoit et génère les résultats. Chaque fois que vous appelez `dotnet test` sans passer --port, il s’exécute en mode console, ce qui provoque l’exécution du Runner en mode console.
2. Au moment du design : utilisé avec d’autres outils, tels que les éditeurs ou les environnements de développement intégré (IDE). Pour plus d’informations sur ce mode, consultez le document concernant le [protocole dotnet-test](test-protocol.md). 

## <a name="options"></a>Options

`[project]`
    
Spécifie le chemin du projet de test. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`-?|-h|--help`

Affiche une aide brève pour la commande.

`--parentProcessId`

Utilisé par l’IDE pour spécifier son ID de processus. Le test s’arrête si le processus parent s’arrête.

`--port`

Utilisé par l’IDE pour spécifier un numéro de port dans le but d’écouter une connexion.

`-c|--configuration <Debug|Release>`

Configuration dans laquelle effectuer la génération. La valeur par défaut est `Release`. 

`-o|--output [OUTPUT_DIRECTORY]`

Répertoire dans lequel rechercher les binaires à exécuter.

`-b|--build-base-path <OUTPUT_DIRECTORY>`

Répertoire dans lequel placer les sorties temporaires.

`-f|--framework [FRAMEWORK]`

Recherche des binaires de test pour un framework spécifique.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Recherche des binaires de test pour le runtime spécifié.

`--no-build` 

Ne génère pas le projet de test avant de l’exécuter. 

## <a name="examples"></a>Exemples

Exécutez les tests du projet dans le répertoire actif :

`dotnet test` 

Exécutez les tests dans le projet test1 :

`dotnet test /projects/test1/project.json` 

## <a name="see-also"></a>Voir aussi

[Protocole de communication dotnet-test](test-protocol.md)

[Frameworks](../../standard/frameworks.md)

[Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)


<!--HONumber=Nov16_HO1-->


