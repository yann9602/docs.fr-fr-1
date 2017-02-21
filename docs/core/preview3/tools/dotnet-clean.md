---
title: Commande dotnet-clean | Microsoft Docs
description: "La commande dotnet-clean nettoie le répertoire actif."
keywords: "dotnet-clean, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 01/31/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 12144def2095246bb6611522b3dbc2d7e441135a

---

#<a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nom 
`dotnet-clean` : Nettoie la sortie d’un projet. 

## <a name="synopsis"></a>Résumé

`dotnet clean [--help] [--output]  [--framework]  
    [--configuration]  [--verbosity]
    [<project>]`

## <a name="description"></a>Description
La commande `dotnet clean` nettoie la sortie de la génération précédente. Comme elle est implémentée en tant que cible MSBuild, le projet sera évalué. Seules les sorties qui ont été créées lors de la génération sont nettoyées. Les dossiers de sorties intermédiaire (`obj`) et final (`bin`) sont tous deux nettoyés. 

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel les fichiers binaires générés ont été placés. Vous devez également définir `--framework` lorsque vous spécifiez cette option. Si vous n’avez pas spécifié cette propriété au moment de la génération, il est inutile de la spécifier pour le nettoyage.

`-f|--framework <FRAMEWORK>`

Infrastructure spécifiée au moment de la génération. Si vous n’avez pas spécifié cette propriété au moment de la génération, il est inutile de la spécifier pour le nettoyage. Le framework doit être défini dans le [fichier projet](csproj.md).

`-c|--configuration [Debug|Release]`

Définit une configuration dans laquelle la génération a été effectuée.  Si aucune valeur n’est spécifiée, la valeur utilisée par défaut est `Debug`. Si vous n’avez pas spécifié cette propriété au moment de la génération, il est inutile de la spécifier pour le nettoyage.

`-v|--verbosity [Quiet|Minimal|Normal|Diag]`

Définit le niveau de détail à utiliser pour l’appel de la commande `dotnet clean`. Les niveaux de détail correspondent aux [niveaux de détail MSBuild](https://msdn.microsoft.com/en-us/library/ms164311.aspx) standard. 


## <a name="examples"></a>Exemples

Nettoyez une génération par défaut du projet :

`dotnet clean`

Nettoyez un projet généré à l’aide de la configuration Release :

`dotnet clean --configuration Release`



<!--HONumber=Feb17_HO2-->


