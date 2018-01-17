---
title: "Utiliser le modèle d’espace de travail du SDK .NET Compiler Platform"
description: "Cette présentation fournit des informations sur le type que vous utilisez pour interroger et manipuler l’espace de travail et les projets dans votre code."
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: d0d4e9c012b025b9393ac34f0833795fca9841d5
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2017
---
# <a name="work-with-a-workspace"></a>Utiliser un espace de travail

La couche des **espaces de travail** est l’emplacement à partir duquel sont effectuées l’analyse de code et la refactorisation dans les solutions entières. Dans cette couche, l’API des espaces de travail vous aide à organiser toutes les informations sur les projets d’une solution dans un modèle objet unique. Ce modèle vous permet d’accéder directement aux modèles objet de la couche du compilateur, tels que le texte source, les arborescences de syntaxe, les modèles sémantiques et les compilations, sans avoir à analyser des fichiers, configurer des options ou gérer des dépendances entre projets. 

Les environnements hôtes, comme un IDE, vous fournissent un espace de travail correspondant à la solution ouverte. Vous pouvez également utiliser ce modèle en dehors d’un IDE, simplement en chargeant un fichier solution.

## <a name="workspace"></a>Espace de travail

Un espace de travail est une représentation active de la solution sous forme de collection de projets, chacun de ces projets contenant une collection de documents. Un espace de travail est généralement lié à un environnement hôte, qui change en permanence à mesure qu’un utilisateur tape ou manipule des propriétés. 

La classe <xref:Microsoft.CodeAnalysis.Workspace> fournit l’accès au modèle actif de la solution. Quand un changement se produit dans l’environnement hôte, l’espace de travail déclenche les événements correspondants, et la propriété <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> est mise à jour. Par exemple, quand un utilisateur tape dans un éditeur de texte correspondant à l’un des documents sources, l’espace de travail déclenche un événement pour signaler que le modèle global de la solution a changé et indiquer quel document a été modifié. Vous pouvez ensuite réagir à ces changements, par exemple, vérifier si le nouveau modèle est correct, surligner les zones d’intérêt ou suggérer une modification du code. 

Vous pouvez également créer des espaces de travail autonomes qui sont déconnectés de l’environnement hôte ou qui sont utilisés dans une application sans environnement hôte.

## <a name="solutions-projects-documents"></a>Solutions, projets, documents

Même si un espace de travail change chaque fois qu’un utilisateur appuie sur une touche, vous pouvez utiliser le modèle de la solution en mode isolation. 

Une solution est un modèle immuable des projets et des documents. Le modèle peut donc être partagé sans verrouillage ni duplication. Après avoir obtenu une instance de la solution à partir de la propriété <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType>, vous ne pouvez plus la changer. Toutefois, comme pour les arborescences de syntaxe et les compilations, vous pouvez modifier des solutions en créant d’autres instances basées sur des solutions existantes et en y apportant les changements souhaités. Pour répercuter vos changements dans l’espace de travail, vous devez explicitement réappliquer la solution modifiée dans l’espace de travail.

Un projet est une composante du modèle de solution immuable global. Il représente l’ensemble des documents du code source, des options d’analyse et de compilation, et des références d’assembly et entre projets. À partir d’un projet, vous pouvez accéder à la compilation correspondante sans avoir besoin de déterminer les dépendances du projet ou d’analyser des fichiers sources.

Un document est une autre composante du modèle de solution immuable global. Un document représente un fichier source unique à partir duquel vous pouvez accéder au texte du fichier, à l’arborescence de syntaxe et au modèle sémantique.

Le diagramme suivant illustre les relations entre l’espace de travail et l’environnement hôte, les outils, et la façon dont les modifications sont effectuées.

![relations entre différents éléments d’un espace de travail contenant des projets et des fichiers sources](media/workspace-obj-relations.png)

## <a name="summary"></a>Récapitulatif

Roslyn expose un ensemble d’API de compilateur et d’API d’espaces de travail. Ces API fournissent des informations détaillées sur votre code source et offrent une haute fidélité avec les langages Visual Basic et C#.  Le SDK .NET Compiler Platform réduit considérablement les difficultés inhérentes à la création d’applications et d’outils axés sur le code. Il offre de nombreuses possibilités d’innovation dans différents champs, notamment la métaprogrammation, la génération et la transformation de code, l’utilisation interactive des langages C# et VB et l’incorporation de C# et de VB dans des langages propres au domaine.  
