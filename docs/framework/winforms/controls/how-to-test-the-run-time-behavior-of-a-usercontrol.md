---
title: "Comment : tester le comportement d'un UserControl au moment de l'exécution"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48b7c47a14f27439c60280a5c4202e9f4af76397
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Comment : tester le comportement d'un UserControl au moment de l'exécution
Lorsque vous développez un <xref:System.Windows.Forms.UserControl>, vous devez tester son comportement au moment de l’exécution. Vous pouvez créer un projet d’application Windows distincts et placer votre contrôle sur un formulaire de test, mais cette procédure n’est pas pratique. Un moyen plus rapide et plus facile consiste à utiliser le **conteneur de Test UserControl** fournis par Visual Studio. Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.  
  
> [!IMPORTANT]
>  Le conteneur de test charger votre <xref:System.Windows.Forms.UserControl>, le contrôle doit avoir au moins un constructeur public.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Un contrôle Visual C++ ne peut pas être testé à l’aide de la **conteneur de Test UserControl**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>Pour tester le comportement d’exécution d’un UserControl  
  
1.  Créer un projet de bibliothèque de contrôles Windows appelé **TestContainerExample**. Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.Label> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.  
  
3.  Appuyez sur F5 pour générer le projet et exécuter le **conteneur de Test UserControl**. Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans les **aperçu** volet.  
  
4.  Sélectionnez le <xref:System.Windows.Forms.Control.BackColor%2A> propriété affichée dans le <xref:System.Windows.Forms.PropertyGrid> contrôle situé à droite de la **aperçu** volet. Modifiez sa valeur en `ControlDark`. Observez que le contrôle devient une couleur plus sombre. Essayez de modifier d’autres valeurs de propriété et observez l’effet sur votre contrôle.  
  
5.  Cliquez sur le **ancrer le contrôle utilisateur remplir** case à cocher ci-dessous le **aperçu** volet. Observez que le contrôle est redimensionné pour remplir le volet. Redimensionner le conteneur de test et observez que le contrôle est redimensionné avec le volet.  
  
6.  Fermez le conteneur de test.  
  
7.  Ajoutez un autre contrôle utilisateur à la **TestContainerExample** projet. Pour plus d’informations, consultez [NIB : Comment : ajouter des éléments existants à un projet](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.  
  
9. Appuyez sur F5 pour générer le projet et exécuter le conteneur de test.  
  
10. Cliquez sur le **sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour basculer entre les deux contrôles utilisateur.  
  
## <a name="testing-user-controls-from-another-project"></a>Contrôles utilisateur à partir d’un autre projet de test  
 Vous pouvez tester les contrôles utilisateur à partir d’autres projets dans le conteneur de test de votre projet actuel.  
  
#### <a name="to-test-user-controls-from-another-project"></a>Pour tester les contrôles utilisateur à partir d’un autre projet  
  
1.  Créer un projet de bibliothèque de contrôles Windows appelé **TestContainerExample2**. Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.RadioButton> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.  
  
3.  Appuyez sur F5 pour générer le projet et exécuter le conteneur de test. Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans les **aperçu** volet.  
  
4.  Cliquez sur le **charge** bouton.  
  
5.  Dans le **ouvrir** boîte de dialogue, accédez à **TestContainerExample**.dll que vous avez créé dans la procédure précédente. Sélectionnez **TestContainerExample**.dll et cliquez sur le **ouvrir** bouton Charger les contrôles utilisateur  
  
6.  Utilisez le **sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour basculer entre les deux contrôles utilisateur à partir de la **TestContainerExample** projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.UserControl>  
 [Guide pratique pour créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Concepteur de contrôles utilisateur](http://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
