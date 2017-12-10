---
title: 'Configuration de projets (F #)'
description: "Découvrez comment utiliser le Concepteur de projet lorsque vous travaillez avec des projets F # dans Visual Studio."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8b2ed206-34e4-4256-a6ce-0c2499561165
ms.openlocfilehash: f56fed1e16b4de1d97766f37cb1c72297d5502d5
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="configuring-projects-in-visual-studio"></a>Configuration de projets dans Visual Studio

> [!NOTE]
Cet article n’est pas à jour avec la dernière version de Visual Studio.  Il sera mis à jour.

Cette rubrique inclut des informations sur l’utilisation de la **Concepteur de projets** lorsque vous travaillez avec des projets F #. Utilisation des projets F # n’est pas significativement différente de celle des projets Visual Basic ou c#. Vous pouvez souvent utiliser la documentation du projet Visual Studio générale comme référence principale lorsque vous utilisez F #. Cette rubrique fournit des liens vers des informations pertinentes dans la documentation de Visual Studio pour les paramètres qui sont partagés avec les autres langages de Visual Studio et décrit également les paramètres spécifiques à F #.

## <a name="project-designer"></a>Concepteur de projets
Le **Concepteur de projets** et son utilisation générale sont entièrement décrites dans la rubrique [Introduction au Concepteur de projet](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) dans la documentation de Visual Studio. Le **Concepteur de projet** se compose de plusieurs pages groupées par fonctionnalités. Les pages sont disponibles pour les projets F # sont un sous-ensemble de celles qui sont disponibles pour d’autres langues. Les pages prises en charge en F # sont décrits dans le tableau suivant. Les pages qui ne sont pas disponibles se rapportent aux fonctionnalités qui ne sont pas disponibles en F #, ou qui ne sont disponibles qu’en modifiant une option de ligne de commande. Les pages qui sont disponibles en F # sont similaires aux c# pages plus près, donc un lien est fourni à pertinentes c# **Concepteur de projets** page.

|Page du Concepteur de projet|Liens connexes|Description|
|---------------------|-------------|-----------|
|`Application`|[Page application, Concepteur de projets &#40; C &#35; &#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Permet de spécifier des paramètres au niveau de l’application et des propriétés, telles que si vous créez une bibliothèque ou un fichier exécutable, quelle version du .NET Framework ciblée par l’application et des informations où la ressource de fichiers que l’application utilisations sont stockées.|
|`Build`|[Build Page, Project Designer &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Vous permet de contrôler comment le code est compilé.|
|`Build Events`|[Build Page événements, Concepteur de projets &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Vous permet de spécifier des commandes à exécuter avant ou après la compilation.|
|`Debug`|[Page Déboguer, Concepteur de projet](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Permet de contrôler la façon dont l’application s’exécute pendant le débogage. Cela inclut tout spécial débogage modes que vous voulez activer, telles que le code natif et SQL et de la ligne de commande à utiliser et quel est le répertoire de démarrage de votre application.|
|`Reference Paths`|[Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)|Vous permet de spécifier où rechercher les assemblys dont dépend le code.|

## <a name="f-specific-settings"></a>F #-paramètres spécifiques
Le tableau suivant résume les paramètres spécifiques à F #:

|Page du Concepteur de projet|Paramètre|Description|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|Si sélectionné, permet l’utilisation de la fin d’instruction Microsoft intermediate language (MSIL). Cela entraîne le frame de pile être réutilisées pour les fonctions récursives tail. Équivalent à la `--tailcalls` option du compilateur.|
|`Build`|`Other flags`|Vous permet de spécifier d’autres options du compilateur de ligne de commande.|

## <a name="see-also"></a>Voir aussi
 [Prise en main) (F # dans Visual Studio](../get-started/get-started-visual-studio.md)  
 [Options du compilateur](../language-reference/compiler-options.md)  
 [Présentation du Concepteur de projets](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
