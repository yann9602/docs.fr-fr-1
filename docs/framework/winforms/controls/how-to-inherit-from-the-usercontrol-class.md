---
title: "Comment : hériter de la classe UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec04e6122f32321c34efe030bfca943baed5bf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Comment : hériter de la classe UserControl
Pour combiner les fonctionnalités d’un ou de plusieurs contrôles Windows Forms avec du code personnalisé, vous pouvez créer un *contrôle utilisateur*. Les contrôles utilisateur allient le développement rapide de contrôles, les fonctionnalités des contrôles Windows Forms standard et la polyvalence des propriétés et méthodes personnalisées. Lorsque vous créez un contrôle utilisateur, un concepteur visible, sur lequel vous pouvez placer des contrôles Windows Forms standard, s’affiche. Ces contrôles conservent toutes leurs fonctionnalités inhérentes, ainsi que l’apparence et le comportement de contrôles standard. Une fois que ces contrôles sont générés dans le contrôle utilisateur, ils ne sont toutefois plus disponibles par le biais du code. Le contrôle utilisateur effectue sa propre peinture et gère également toutes les fonctionnalités de base associées aux contrôles.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-user-control"></a>Pour créer un contrôle utilisateur  
  
1.  Créez un projet de **bibliothèque de contrôles Windows**.  
  
     Un projet est créé avec un contrôle utilisateur vide.  
  
2.  Faites glisser des contrôles de l’onglet **Windows Forms** de la **boîte à outils** vers votre concepteur.  
  
3.  Positionnez et concevez ces contrôles comme vous souhaitez qu’ils apparaissent dans le contrôle utilisateur final. Si vous souhaitez permettre aux développeurs d’accéder aux contrôles constitutifs, vous devez les déclarer publics ou exposer de manière sélective les propriétés du contrôle constitutif. Pour plus d’informations, consultez [Comment : exposer les propriétés des contrôles constitutifs](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.  
  
5.  Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**. Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Guide pratique pour hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Guide pratique pour hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Guide pratique pour créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Dépannage des gestionnaires d’événements hérités en Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
