---
title: "Comment&#160;: tester le comportement d&#39;un UserControl au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "contrôles composites, tester"
  - "contrôles utilisateur (Windows Forms), tester"
  - "UserControl (classe), comportement au moment de l'exécution"
  - "UserControl (classe), tester"
  - "conteneur de test UserControl"
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: tester le comportement d&#39;un UserControl au moment de l&#39;ex&#233;cution
Lorsque vous développez un <xref:System.Windows.Forms.UserControl>, vous devez tester son comportement à l'exécution.  Vous pouvez créer un projet d'application Windows séparé et placer votre contrôle sur un formulaire de test, mais cette procédure est gênante.  Une approche plus rapide et plus facile est d'utiliser le **conteneur de test UserControl** fourni par Visual Studio.  Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.  
  
> [!IMPORTANT]
>  Pour que le conteneur de test charge votre <xref:System.Windows.Forms.UserControl>, le contrôle doit avoir au moins un constructeur public.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Vous ne pouvez pas tester un contrôle Visual C\+\+ à l'aide du **conteneur de test UserControl**.  
  
### Pour tester le comportement à l'exécution d'un UserControl  
  
1.  Créez un projet de bibliothèque de contrôles Windows appelé TestContainerExample.  Pour plus d'informations, consultez [Windows Control Library Template](http://msdn.microsoft.com/fr-fr/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Dans le **Concepteur Windows Forms Designer**, faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **Boîte à outils** sur l'aire de conception du contrôle.  
  
3.  Appuyez sur F5 pour générer le projet et exécuter le **conteneur de test UserControl**.  Le conteneur de test apparaît avec votre <xref:System.Windows.Forms.UserControl> dans le volet **Aperçu**.  
  
4.  Sélectionnez la propriété <xref:System.Windows.Forms.Control.BackColor%2A> affichée dans le contrôle <xref:System.Windows.Forms.PropertyGrid> à droite du volet **Aperçu**.  Modifiez sa valeur en `ControlDark`.  Notez que le contrôle prend une couleur plus sombre.  Essayez de modifier d'autres valeurs de propriété et observez l'effet sur votre contrôle.  
  
5.  Cliquez sur la case à cocher **Appliquer la valeur Fill à la propriété Dock au contrôle utilisateur** au\-dessous du volet **Aperçu**.  Observez que le contrôle est redimensionné pour remplir le volet.  Redimensionnez le conteneur de test et observez que le contrôle est redimensionné avec le volet.  
  
6.  Fermez le conteneur de test.  
  
7.  Ajoutez un autre contrôle utilisateur au projet TestContainerExample.  Pour plus d'informations, consultez [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/fr-fr/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  Dans le **concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** sur l'aire de conception du contrôle.  
  
9. Appuyez sur F5 pour générer le projet et exécuter le conteneur de test.  
  
10. Cliquez sur **Sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour commuter entre les deux contrôles utilisateur.  
  
## Test des contrôles utilisateur à partir d'un autre projet  
 Vous pouvez tester des contrôles utilisateur à partir d'autres projets dans le conteneur de test de votre projet actuel.  
  
#### Pour tester des contrôles utilisateur à partir d'un autre projet  
  
1.  Créez un projet de bibliothèque de contrôles Windows appelé TestContainerExample2.  Pour plus d'informations, consultez [Windows Control Library Template](http://msdn.microsoft.com/fr-fr/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Dans le **concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.RadioButton> de la **Boîte à outils** sur l'aire de conception du contrôle.  
  
3.  Appuyez sur F5 pour générer le projet et exécuter le conteneur de test.  Le conteneur de test apparaît avec votre <xref:System.Windows.Forms.UserControl> dans le volet **Aperçu**.  
  
4.  Cliquez sur le bouton **Charger**.  
  
5.  Dans la boîte de dialogue **Ouvrir**, naviguez jusqu'à TestContainerExample.dll que vous avez construit dans la procédure précédente.  Sélectionnez TestContainerExample.dll et cliquez sur le bouton **Ouvrir** pour charger les contrôles utilisateur.  
  
6.  Utilisez **Sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour commuter entre les deux contrôles utilisateur du projet TestContainerExample.  
  
## Voir aussi  
 <xref:System.Windows.Forms.UserControl>   
 [Comment : créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C\#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [User Control Designer](http://msdn.microsoft.com/fr-fr/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)