---
title: "Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 691487046e2a34dbf233dc4bc03e20f9ec245da1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés
Si vos composants sont définis par un projet dans la solution actuellement ouverte, ils apparaissent automatiquement dans le **boîte à outils**, sans aucune action requise par vous. Vous pouvez également remplir manuellement la **boîte à outils** avec vos composants personnalisés à l’aide de la [choisir de boîte de dialogue des éléments de boîte à outils (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb), mais la **boîte à outils** tient compte des éléments dans de votre solution génération avec toutes les caractéristiques suivantes :  
  
-   Implémente <xref:System.ComponentModel.IComponent>;  
  
-   N’a pas <xref:System.ComponentModel.ToolboxItemAttribute> la valeur `false`;  
  
-   N’a pas <xref:System.ComponentModel.DesignTimeVisibleAttribute> la valeur `false`.  
  
> [!NOTE]
>  Le **boîte à outils** ne suit pas les chaînes de référence, il n’affichera pas les éléments qui ne sont pas générés par un projet dans votre solution.  
  
 Cette procédure pas à pas montre comment un composant personnalisé apparaît automatiquement dans le **boîte à outils** une fois que le composant est créé. Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Windows Forms.  
  
-   Création d’un composant personnalisé.  
  
-   Création d’une instance d’un composant personnalisé.  
  
-   Déchargement et le rechargement d’un composant personnalisé.  
  
 Lorsque vous avez terminé, vous verrez que le **boîte à outils** est remplie avec un composant que vous avez créés.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’application Windows appelé `ToolboxExample`.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Ajoutez un nouveau composant au projet. Appelez-le `DemoComponent`.  
  
     Pour plus d’informations, consultez [NIB : Comment : ajouter de nouveaux éléments de projet](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Générez le projet.  
  
4.  À partir de la **outils** menu, cliquez sur le **Options** élément. Cliquez sur **général** sous le **Concepteur Windows Forms** d’élément et vérifiez que le **AutoToolboxPopulate a** option est définie sur **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Création d’une Instance d’un composant personnalisé  
 L’étape suivante consiste à créer une instance du composant personnalisé sur le formulaire. Étant donné que la **boîte à outils** automatiquement des comptes pour le nouveau composant, c’est aussi simple que la création de tout autre composant ou contrôle.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>Pour créer une instance d’un composant personnalisé  
  
1.  Ouvrez le formulaire du projet dans le **Concepteur Forms**.  
  
2.  Dans le **boîte à outils**, cliquez sur le nouvel onglet appelé **Composants ToolboxExample**.  
  
     Une fois que vous cliquez sur l’onglet, vous verrez **DemoComponent**.  
  
    > [!NOTE]
    >  Pour des raisons de performances, les composants dans la zone et rempli automatiquement de la **boîte à outils** n’affichent pas de bitmaps personnalisées et le <xref:System.Drawing.ToolboxBitmapAttribute> n’est pas pris en charge. Pour afficher une icône pour un composant personnalisé dans le **boîte à outils**, utilisez le **choisir des éléments de boîte à outils** boîte de dialogue pour charger votre composant.  
  
3.  Faites glisser votre composant sur votre formulaire.  
  
     Une instance du composant est créée et ajoutée à la **barre d’état du composant**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Décharger et recharger un composant personnalisé  
 Le **boîte à outils** compte des composants dans chaque chargé de projet, et lorsqu’un projet est déchargé, elle supprime les références aux composants du projet.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Pour tester l’effet sur la boîte à outils de décharger et recharger des composants  
  
1.  Décharger le projet à partir de la solution.  
  
     Pour plus d’informations sur le déchargement de projets, consultez [NIB : Comment : décharger et recharger des projets](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b). Si vous êtes invité à enregistrer, choisissez **Oui**.  
  
2.  Ajouter un nouveau **Application Windows** projet à la solution. Ouvrez le formulaire dans le **concepteur**.  
  
     Le **Composants ToolboxExample** onglet dans le projet précédent est désormais disparu.  
  
3.  Recharger la `ToolboxExample` projet.  
  
     Le **Composants ToolboxExample** onglet maintenant s’affiche de nouveau.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas montre que la **boîte à outils** tient compte des composants d’un projet, mais la **boîte à outils** tient également compte des contrôles. Faites des essais avec vos propres contrôles personnalisés en ajoutant et supprimant des projets de contrôles à partir de votre solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Général, Concepteur Windows Forms, boîte de dialogue Options](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [Comment : manipuler des onglets de boîte à outils](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Placement de contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
