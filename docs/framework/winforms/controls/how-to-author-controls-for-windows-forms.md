---
title: "Comment : créer des contrôles pour des Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f42ee49a4690c23a563740993e721207d5dedea0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-controls-for-windows-forms"></a>Comment : créer des contrôles pour des Windows Forms
Un contrôle désigne un lien graphique entre l’utilisateur et le programme. Un contrôle peut fournir ou traiter des données, accepter des entrées d’utilisateur, répondre à des événements ou effectuer de nombreuses autres fonctions afin de connecter l’utilisateur et l’application. Un contrôle étant essentiellement un composant doté d’une interface graphique, il peut servir n’importe quelle fonction d’un composant, mais aussi fournir une interaction utilisateur. Les contrôles sont utilisés à des fins spécifiques, et la création de contrôles représente simplement une autre tâche de programmation. Dans cette optique, les étapes suivantes constituent une vue d’ensemble du processus de création de contrôle. Les liens renvoient vers des informations supplémentaires concernant les étapes individuelles.  
  
> [!NOTE]
>  Si vous souhaitez créer un contrôle personnalisé à utiliser sur des Web Forms, consultez [Développement de contrôles serveur ASP.NET personnalisés](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-control"></a>Pour créer un contrôle  
  
1.  Déterminez ce que votre contrôle devra accomplir ou le rôle qu’il jouera dans votre application. Tenez compte des facteurs suivants :  
  
    -   De quel type d’interface graphique avez-vous besoin ?  
  
    -   Quelles interactions utilisateur spécifiques ce contrôle gérera-t-il ?  
  
    -   La fonctionnalité dont vous avez besoin est-elle fournie par des contrôles existants ?  
  
    -   Pouvez-vous obtenir la fonctionnalité dont vous avez besoin en combinant plusieurs contrôles Windows Forms ?  
  
2.  Si vous avez besoin d’un modèle d’objet pour votre contrôle, déterminez comment la fonctionnalité sera distribuée dans tout le modèle d’objet et répartissez-la entre le contrôle et les éventuels sous-objets. Un modèle d’objet peut être utile si vous prévoyez un contrôle complexe ou si vous souhaitez incorporer plusieurs fonctionnalités.  
  
3.  Déterminez le type de contrôle (par exemple, contrôle utilisateur, contrôle personnalisé, contrôle Windows Forms hérité) dont vous avez besoin. Pour plus d’informations, consultez [Recommandations relatives au type du contrôle](../../../../docs/framework/winforms/controls/control-type-recommendations.md) et [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Présentez les fonctionnalités en tant que propriétés, méthodes et événements du contrôle et de ses sous-objets ou structures secondaires, et assignez des niveaux d’accès appropriés (par exemple, public, protégé, etc.).  
  
5.  Si vous avez besoin d’une peinture personnalisée pour votre contrôle, ajoutez du code. Pour plus d’informations, consultez [Peinture et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Si votre contrôle hérite <xref:System.Windows.Forms.UserControl>, vous pouvez tester son comportement d’exécution par la génération du projet de contrôle et de son exécution dans le **conteneur de Test UserControl**. Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Vous pouvez également tester et déboguer votre contrôle en créant un projet, comme une application Windows, et en le plaçant dans un conteneur. Ce processus est présenté dans [Procédure pas à pas : création d’un contrôle composite à l’aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  À chaque ajout de fonctionnalité, ajoutez des fonctionnalités à votre projet de test pour tester cette nouvelle fonctionnalité.  
  
9. Répétez l’opération en affinant le design.  
  
10. Empaquetez et déployez votre contrôle. Pour plus d’informations, consultez [Déploiement d’applications, de services et de composants](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Comment : hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Guide pratique pour hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Guide pratique pour hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
