---
title: "Procédure pas à pas : création de votre première application Touch"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08f4004329d15b527a889cd7b437a7f18278fc79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Procédure pas à pas : création de votre première application Touch
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]permet aux applications réponde aux entrées tactiles. Par exemple, vous pouvez interagir avec une application en utilisant l’une ou plusieurs doigts sur un périphérique tactile, par exemple un écran tactile que cette procédure pas à pas crée une application qui permet à l’utilisateur à déplacer, redimensionnement ou faire pivoter un objet unique à l’aide des fonctions tactiles.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Un périphérique qui accepte une entrée, par exemple un écran tactile, qui prend en charge l’interface tactile Windows tactile.  
  
 En outre, vous devez avoir une compréhension de base de la création d’une application dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en particulier comment s’abonner à et gérer un événement. Pour plus d’informations, consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Création de l’application  
  
#### <a name="to-create-the-application"></a>Pour créer l'application  
  
1.  Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `BasicManipulation`. Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Remplacez le contenu de MainWindow.xaml par le code XAML suivant.  
  
     Ce balisage crée une application simple qui contient une croix rouge <xref:System.Windows.Shapes.Rectangle> sur un <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.UIElement.IsManipulationEnabled%2A> propriété de la <xref:System.Windows.Shapes.Rectangle> est définie sur true afin qu’il reçoive les événements de manipulation. L’application s’abonne à la <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, et <xref:System.Windows.UIElement.ManipulationInertiaStarting> événements. Ces événements contiennent la logique pour déplacer le <xref:System.Windows.Shapes.Rectangle> lorsque l’utilisateur manipule.  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="BasicManipulation.MainWindow"` avec `x:Class="MainWindow"`.  
  
4.  Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.UIElement.ManipulationStarting> Gestionnaire d’événements.  
  
     Le <xref:System.Windows.UIElement.ManipulationStarting> événement se produit lorsque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] détecte cette touche entrée commence à manipuler un objet. Le code spécifie que la position de la manipulation doit être relative à la <xref:System.Windows.Window> en définissant le <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriété.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.Input.ManipulationDelta> Gestionnaire d’événements.  
  
     Le <xref:System.Windows.Input.ManipulationDelta> événement se produit lorsque l’entrée tactile modifie la position et peut se produire plusieurs fois pendant une manipulation. L’événement peut également se produire après le déclenche d’un doigt. Par exemple, si l’utilisateur fait glisser un doigt sur un écran, le <xref:System.Windows.Input.ManipulationDelta> événement se produit plusieurs fois en tant que le déplacement du doigt. Lorsque l’utilisateur enlève un doigt de l’écran, le <xref:System.Windows.Input.ManipulationDelta> événement continue de se produire pour simuler l’inertie.  
  
     Le code s’applique le <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> à la <xref:System.Windows.UIElement.RenderTransform%2A> de la <xref:System.Windows.Shapes.Rectangle> pour déplacer tandis que l’utilisateur déplace la fonction tactile d’entrée. Il vérifie également si le <xref:System.Windows.Shapes.Rectangle> en dehors des limites de la <xref:System.Windows.Window> lorsque l’événement se produit pendant l’inertie. Si, par conséquent, l’application appelle la <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> méthode à la fin de la manipulation.  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.UIElement.ManipulationInertiaStarting> Gestionnaire d’événements.  
  
     Le <xref:System.Windows.UIElement.ManipulationInertiaStarting> événement se produit lorsque l’utilisateur déclenche tous les doigts de l’écran. Le code définit la rapidité initiale et la décélération pour le déplacement, d’extension et de rotation du rectangle.  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  Générez et exécutez le projet.  
  
     Vous devez voir un carré rouge apparaît dans la fenêtre.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Pour tester l’application, essayez les manipulations suivantes. Notez que vous pouvez effectuer plusieurs des opérations suivantes en même temps.  
  
-   Pour déplacer le <xref:System.Windows.Shapes.Rectangle>, mettez un doigt sur le <xref:System.Windows.Shapes.Rectangle> et déplacez le doigt sur l’écran.  
  
-   Pour redimensionner le <xref:System.Windows.Shapes.Rectangle>, placez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et rapprochez-les ou loin indépendamment les uns des autres.  
  
-   Pour faire pivoter le <xref:System.Windows.Shapes.Rectangle>, placez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et faites pivoter les doigts autour de l’autre.  
  
 Pour provoquer l’inertie, enlevez rapidement vos doigts à partir de l’écran que vous exécutez les manipulations précédentes. Le <xref:System.Windows.Shapes.Rectangle> continuera à déplacer, redimensionner ou faire pivoter pendant quelques secondes avant de s’arrêter.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
