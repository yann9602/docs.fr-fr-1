---
title: "Proc&#233;dure pas &#224; pas&#160;: remplissage automatique de la bo&#238;te &#224; outils avec des composants personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "composants personnalisés, ajouter à la boîte à outils"
  - "IToolboxService (interface)"
  - "boîtes à outils (Windows Forms), remplir"
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Proc&#233;dure pas &#224; pas&#160;: remplissage automatique de la bo&#238;te &#224; outils avec des composants personnalis&#233;s
Si vos composants sont définis par un projet dans la solution actuellement ouverte, ils apparaîtront automatiquement dans la **Boîte à outils**, sans intervention de votre part.  Vous pouvez également remplir manuellement la **Boîte à outils** avec vos composants personnalisés en utilisant le [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/bd07835f-18a8-433e-bccc-7141f65263bb), mais la **Boîte à outils** tient compte, dans les sorties de génération de votre solution, des éléments ayant toutes les caractéristiques suivantes :  
  
-   Implémente <xref:System.ComponentModel.IComponent> ;  
  
-   N'a pas <xref:System.ComponentModel.ToolboxItemAttribute> défini avec la valeur `false` ;  
  
-   N'a pas <xref:System.ComponentModel.DesignTimeVisibleAttribute> défini avec la valeur `false`.  
  
> [!NOTE]
>  La **Boîte à outils** ne suit pas de chaînes de référence ; elle n'affiche donc pas les éléments qui ne sont pas construits par un projet dans votre solution.  
  
 Cette procédure pas à pas montre comment un composant personnalisé peut apparaître automatiquement dans la **Boîte à outils** une fois le composant créé.  Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms.  
  
-   Création d'un composant personnalisé.  
  
-   Création d'une instance d'un composant personnalisé.  
  
-   Déchargement et rechargement d'un composant personnalisé.  
  
 Lorsque vous avez terminé, vous constatez que la **Boîte à outils** est remplie avec un composant que vous avez créé.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé `ToolboxExample`.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Ajoutez un nouveau composant au projet.  Appelez\-le `DemoComponent`.  
  
     Pour plus d'informations, consultez [NIB:How to: Add New Project Items](http://msdn.microsoft.com/fr-fr/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Générez le projet.  
  
4.  Dans le menu **Outils**, cliquez sur l'élément **Options**.  Cliquez sur **Général** sous l'élément **Concepteur Windows Forms** et vérifiez que l'option **AutoToolboxPopulate** a la valeur **True**.  
  
## Création d'une instance d'un composant personnalisé  
 L'étape suivante consiste à créer une instance du composant personnalisé sur le formulaire.  Dans la mesure où la **Boîte à outils** tient automatiquement compte du nouveau composant, cette approche est aussi facile à mettre en œuvre que la création de n'importe quel autre composant ou contrôle.  
  
#### Pour créer une instance d'un composant personnalisé  
  
1.  Ouvrez le formulaire du projet dans le **Concepteur Forms**.  
  
2.  Dans la **Boîte à outils**, cliquez sur le nouvel onglet nommé **Composants ToolboxExample**.  
  
     Une fois que vous cliquez sur l'onglet, **DemoComponent** apparaît.  
  
    > [!NOTE]
    >  Pour des raisons de performances, les composants dans la zone à remplissage automatique de la **Boîte à outils** n'affichent pas de bitmaps personnalisées, et le <xref:System.Drawing.ToolboxBitmapAttribute> n'est pas pris en charge.  Pour afficher une icône pour un composant personnalisé dans la **Boîte à outils**, utilisez la boîte de dialogue **Choisir des éléments de boîte à outils** pour charger votre composant.  
  
3.  Faites glisser votre composant sur votre formulaire.  
  
     Une instance du composant est créée et ajoutée à la **barre d'état des composants**.  
  
## Déchargement et rechargement d'un composant personnalisé  
 La **Boîte à outils** tient compte des composants dans chaque projet chargé, et lorsqu'un projet est déchargé, elle supprime les références aux composants du projet.  
  
#### Pour tester l'effet de déchargement et de rechargement des composants sur la Boîte à outils  
  
1.  Déchargez le projet de la solution.  
  
     Pour plus d'informations sur le déchargement de projets, consultez [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/fr-fr/abc0155b-8fcb-4ffc-95b6-698518a7100b).  Si vous êtes invité à enregistrer, choisissez **Oui**.  
  
2.  Ajoutez un nouveau projet **Application Windows** à la solution.  Ouvrez le formulaire dans le **concepteur**.  
  
     L'onglet **Composants ToolboxExample** du projet précédent a maintenant disparu.  
  
3.  Rechargez le projet `ToolboxExample`.  
  
     L'onglet **Composants ToolboxExample** réapparaît maintenant.  
  
## Étapes suivantes  
 Cette procédure pas à pas montre que la **Boîte à outils** prend compte les composants d'un projet, mais la **Boîte à outils** tient également compte des contrôles.  Essayez avec vos propres contrôles personnalisés en ajoutant et supprimant des projets de contrôle de votre solution.  
  
## Voir aussi  
 [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8dd170af-72f0-4212-b04b-034ceee92834)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/fr-fr/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Placement de contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)