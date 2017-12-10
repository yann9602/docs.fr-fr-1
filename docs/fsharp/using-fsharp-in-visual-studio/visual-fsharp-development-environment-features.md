---
title: "Fonctionnalités de l’environnement de développement F#"
description: "Découvrez les fonctionnalités de Visual Studio 2012 sont pris en charge en F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 809e9a34-b271-4c87-8356-2426b44f4721
ms.openlocfilehash: 05727bf11eccfd64f823dd280b1a19210815ca5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="visual-f-development-environment-features"></a>Fonctionnalités de l’environnement de développement Visual F#

> [!NOTE]
Cet article n’est pas à jour avec la dernière version de Visual Studio.  Il sera mis à jour.

Cette rubrique contient des informations sur les fonctionnalités de Visual Studio 2012 sont pris en charge en F #.

## <a name="project-features"></a>Fonctionnalités de projet
Le tableau suivant résume les modèles qui sont disponibles pour une utilisation dans les projets F #. Pour plus d’informations sur les modèles de projet et d’élément, consultez [NIB création de projets à partir de modèles](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2).

|Type de modèle|Description|Modèles pris en charge|
|-------------|-----------|-------------------|
|Modèles de projet|Types de projets disponibles dans le **nouveau projet** boîte de dialogue.|<ul><li>Application F #<br /></li><li>Bibliothèque F #<br /></li><li>Didacticiel F #<br /></li><li>Bibliothèque de F # Portable<br /></li><ul/>|
|Modèles d’élément|Types de fichiers disponibles dans le **ajouter un nouvel élément** boîte de dialogue.|<ul><li>Fichier source F # (.fs)<br /></li><li>Script F # (.fsx)<br /></li><li>Fichier de signature F # (.fsi)<br /></li><li>Fichier de configuration (.config)<br /></li><li>Connexion de base de données SQL (fournisseur de type LINQ to SQL)<br /></li><li>Connexion de base de données SQL (fournisseur LINQ to Entities type)<br /></li><li>Connexion au Service OData (fournisseur de type LINQ)<br /></li><li>Connexion au Service WSDL (fournisseur de type)<br /></li><li>Fichier XML (.xml)<br /></li><li>Fichier texte<br /></li><ul/>|
Pour créer une application qui peut fonctionner comme un exécutable autonome, choisissez le type de projet Application F #. Pour créer une bibliothèque (autrement dit, un assembly managé ou. Fichier DLL) pour une utilisation sur la plateforme de bureau Windows, choisissez la bibliothèque F #. Pour créer une bibliothèque portable qui peut être utilisée sur n’importe quelle plateforme prise en charge, choisissez la bibliothèque F # Portable. Les projets de bibliothèque F # Portable référencent une version de FSharp.Core.dll est appropriée créer une bibliothèque F # qui peut être utilisée avec les applications qui s’exécutent sur des plateformes, telles que les applications du Windows Store, le .NET Framework 4.5, Xamarin.iOS et Xamarin.Android.

Pour plus d’informations sur les modèles d’élément pour accéder aux données, consultez [fournisseurs de Type](../tutorials/type-providers/index.md).

Le tableau suivant récapitule les fonctionnalités de propriétés de projet pris en charge et non pris en charge en F #. Pour plus d’informations, consultez [configuration des projets](configuring-projects.md) et [Introduction au Concepteur de projet](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7).

|Paramètres de projet|Prise en charge en F #?|Notes|
|---------------|----------------|-----|
|Fichiers de ressources|Oui||
|Génération, débogage et les paramètres de référence|Oui||
|Multi-ciblage|Oui||
|Icône et manifeste|Non|Disponible via les options de ligne de commande du compilateur.|
|Client des Services ASP.NET|Non||
|ClickOnce|Non|Utilisez un projet client dans un autre langage .NET Framework, le cas échéant.|
|Nom fort|Non|Disponible via les options de ligne de commande du compilateur.|
|Assembly de publication et le contrôle de version|Non||
|Analyse du code|Non|Outils d’analyse de code peuvent être exécutés manuellement ou en tant que partie d’une commande post-build.|
|Sécurité (modifier les niveaux de confiance)|Non||

## <a name="code-and-text-editor-features"></a>Code et les fonctionnalités de l’éditeur de texte
Les fonctionnalités suivantes des éditeurs de texte Visual Studiocode sont pris en charge en F #. Pour obtenir des informations générales sur la modification du code dans Visual Studio et les fonctionnalités de l’éditeur de texte, consultez [l’écriture de Code dans l’éditeur de texte et le Code](/visualstudio/ide/writing-code-in-the-code-and-text-editor).

|Fonctionnalité|Description|Prise en charge en F #?|
|-------|-----------|----------------|
|Commentaire automatiquement|Permet d’ajouter ou supprimer les commentaires des sections de code.|Oui|
|Mise en forme automatique|Remet en forme du code de mise en retrait standard et un style.|Non|
|Signets|Permet d’enregistrer des emplacements dans l’éditeur.|Oui|
|Modifier la mise en retrait|Met en retrait ou annule un retrait des lignes sélectionnées.|Oui|
|[Recherche et remplacement de texte](/visualstudio/ide/finding-and-replacing-text)|Permet d’effectuer une recherche dans un fichier, un projet ou une solution et potentiellement modifier texte.|Oui|
|Atteindre la définition pour API .NET Framework|Lorsque le curseur est positionné sur une API .NET Framework, affiche le code généré à partir des métadonnées de .NET Framework.|Non|
|Atteindre la définition pour API définie par l’utilisateur|Lorsque le curseur se trouve sur une entité de programme que vous avez définie, déplace le curseur à l’emplacement où l’entité est définie dans votre code.|Oui|
|Atteindre la ligne|Permet d’accéder à une ligne spécifique dans un fichier, par numéro de ligne.|Oui|
|Barres de navigation en haut du fichier|Permet d’accéder à des emplacements dans le code, en, par exemple, nom de la fonction.|Oui|
|Mode Plan ; Consultez [mise en relief](/visualstudio/ide/outlining).|Vous permet de réduire des sections de votre code pour créer une vue plus compacte.|Oui|
|Remplacer par des tabulations|Convertit les espaces en tabulations.|Oui|
|Colorisation de type|Affiche le nom des types définis dans une couleur spécifique.|Oui|
|Recherche rapide. Consultez Recherche rapide, fenêtre Rechercher et remplacer.|Permet d’effectuer une recherche dans un fichier ou un projet.|Oui|

## <a name="intellisense-features"></a>Fonctionnalités IntelliSense
Le tableau suivant récapitule les fonctionnalités IntelliSense prises en charge et non pris en charge en F #. Pour obtenir des informations générales sur IntelliSense, consultez [utilisation d’IntelliSense](/visualstudio/ide/using-intellisense).

|Fonctionnalité|Description|Prise en charge en F #?|
|-------|-----------|----------------|
|Implémenter des interfaces|Génère des stubs de code pour les méthodes d’interface.|Non|
|Extraits de code|Injecte le code à partir d’une bibliothèque de constructions de programmation courantes dans les rubriques.|Non|
|Compléter le mot|Termine les mots et de noms en cours de frappe.|Oui|
|Mode de saisie semi-automatique d’utiliser d’abord|Activée, oblige l’achèvement de word sélectionner la première correspondance que vous tapez, au lieu d’attendre pour vous permettre de sélectionner un ou appuyez sur **CTRL + espace**.|Non|
|Générer des éléments de code|Vous permet de générer un code stub pour diverses constructions.|Non|
|Liste des membres|Lorsque vous tapez l’opérateur d’accès au membre (.), affiche les membres d’un type.|Oui|
|Organiser les instructions Using/ouvrir|Organise les espaces de noms référencés par **à l’aide de** instructions en c# ou **ouvrir** directives en F #.|Non|
|Informations sur les paramètres|Affiche des informations utiles sur les paramètres que vous tapez un appel de fonction.|Oui|
|Info express|Affiche la déclaration complète de tout identificateur présent dans votre code.|Oui|
Refactorisation du code F # n’est pas pris en charge dans Visual Studio 2012.

## <a name="debugging-features"></a>Fonctionnalités de débogage
Le tableau suivant récapitule les fonctionnalités qui sont disponibles lorsque vous déboguez du code F #. Pour obtenir des informations générales sur le débogueur Visual Studio, consultez [débogage dans Visual Studio](https://msdn.microsoft.com/library/sc65sadd.aspx).

|Fonctionnalité|Description|Prise en charge en F #?|
|-------|-----------|----------------|
|Automatique (fenêtre)|Affiche les variables automatiques ou temporaires.|Non|
|Points d'arrêt|Vous permet de suspendre l’exécution de code à des points spécifiques pendant le débogage.|Oui|
|Points d’arrêt conditionnels|Active les points d’arrêt qui testent une condition qui détermine si l’exécution doit être suspendue.|Oui|
|Modifier & Continuer|Permet au code d’être modifié et compilée comme vous déboguez un programme en cours d’exécution sans arrêter et redémarrer le débogueur.|Non|
|Évaluateur d’expression|Évalue et exécute le code au moment de l’exécution.|Non, mais le c# évaluateur d’expression peut être utilisé, bien que vous devez utiliser la syntaxe c#.|
|Débogage d’historique|Vous permet de pas à pas dans le code exécuté précédemment.|Oui|
|Fenêtre Variables locales|Montre localement défini les variables et les valeurs.|Oui|
|Exécuter jusqu'au curseur|Vous permet d’exécuter le code jusqu'à ce que la ligne qui contient le curseur est atteint.|Oui|
|Pas à pas détaillé|Vous permet de faire progresser l’exécution et la déplacer dans un appel de fonction.|Oui|
|Pas à pas principal|Vous permet de faire progresser l’exécution dans le frame de pile actuel et se déplace après un appel de fonction.|Oui|

## <a name="additional-tools"></a>Outils supplémentaires
Le tableau suivant récapitule la prise en charge pour F # de Visual Studio tools.

|Outil|Description|Prise en charge en F #?|
|----|-----------|----------------|
|Hiérarchie d'appels|Affiche la structure imbriquée de la fonction appelle dans votre code.|Non|
|Métrique du code|Rassemble des informations relatives à votre code, comme le nombre de lignes.|Non|
|Affichage de classes|Fournit une vue basée sur le type du code dans un projet.|Non|
|[Liste d’erreurs, fenêtre](/visualstudio/ide/reference/error-list-window)|Affiche une liste d’erreurs dans le code.|Oui|
|[F# Interactive](../tutorials/fsharp-interactive/index.md)|Vous permet de taper (ou copier et coller) F # de code et exécutez immédiatement, indépendamment de la génération de votre projet. La fenêtre F # Interactive est une lecture, l’évaluer, la boucle d’impression (REPL).|Oui|
|Explorateur d'objets|Permet d’afficher les types dans un assembly.|Types F # tels qu’ils apparaissent dans des assemblys compilés n’apparaissent pas exactement comme vous les avez créés. Vous pouvez parcourir la représentation compilée des types F #, mais vous ne pouvez pas afficher les types de telles qu’elles apparaissent à partir de F #.|
|[Sortie (fenêtre)](/visualstudio/ide/reference/output-window)|Affiche la sortie de build.|Oui|
|Analyse des performances|Fournit des outils pour mesurer les performances de votre code.|Oui|
|Fenêtre Propriétés|Affiche et permet la modification des propriétés de l’objet dans l’environnement de développement qui a le focus.|Oui|
|[Explorateur de serveurs](https://msdn.microsoft.com/library/x603htbk.aspx)|Fournit des méthodes pour interagir avec un large éventail de ressources du serveur.|Oui|
|Explorateur de solutions|Permet d’afficher et gérer des projets et des fichiers.|Oui|
|Liste des tâches|Vous permet de gérer les éléments de travail se rapportant à votre code.|Oui|
|Projets de test|Fournit des fonctionnalités qui vous aident à tester votre code.|Non|
|Boîte à outils|Affiche les onglets contenant des objets déplaçables tels que des contrôles et des sections de texte ou de code.|Oui|

## <a name="see-also"></a>Voir aussi
 [Prise en main) (F # dans Visual Studio](../get-started/get-started-visual-studio.md)  
 [Configuration de projets](configuring-projects.md)  
