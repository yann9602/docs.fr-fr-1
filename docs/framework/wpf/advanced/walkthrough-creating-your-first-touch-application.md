---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premi&#232;re application Touch | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "créer une application à écran tactile (WPF)"
  - "créer une application à sensibilité tactile (WPF)"
  - "applications à écran tactile (WPF), créer"
  - "applications à sensibilité tactile (WPF), créer"
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premi&#232;re application Touch
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] active la sensibilité tactile des applications.  Par exemple, vous pouvez interagir avec une application en utilisant un ou plusieurs doigts sur un périphérique avec sensibilité tactile, tel qu'un écran tactile. Cette procédure pas à pas crée une application qui permet à l'utilisateur de déplacer, redimensionner ou faire pivoter un objet unique à l'aide de fonctions tactiles.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   périphérique qui accepte les entrées tactiles, tel qu'un écran tactile, qui prend en charge l'interface tactile Windows.  
  
 En outre, vous devez avoir une connaissance de base sur la création d'une application dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en particulier sur la façon de s'abonner à un événement et de le gérer.  Pour plus d'informations, consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## Création de l'application  
  
#### Pour créer l'application  
  
1.  Créez un projet d'application WPF dans Visual Basic ou Visual C\# nommé `ManipulationDeBase`.  Pour plus d'informations, consultez [Comment : créer un projet d'application WPF](http://msdn.microsoft.com/fr-fr/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Remplacez le contenu de MainWindow.xaml par le code XAML suivant.  
  
     Ce balisage crée une application simple qui contient un <xref:System.Windows.Shapes.Rectangle> rouge sur un <xref:System.Windows.Controls.Canvas>.  La propriété <xref:System.Windows.UIElement.IsManipulationEnabled%2A> du <xref:System.Windows.Shapes.Rectangle> a la valeur true afin qu'il reçoive les événements de manipulation.  L'application s'abonne aux événements <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta> et <xref:System.Windows.UIElement.ManipulationInertiaStarting>.  Ces événements contiennent la logique permettant de déplacer le <xref:System.Windows.Shapes.Rectangle> lorsque l'utilisateur le manipule.  
  
     [!code-xml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="BasicManipulation.MainWindow"` par `x:Class="MainWindow"`.  
  
4.  Dans la classe `MainWindow`, ajoutez le gestionnaire d'événements <xref:System.Windows.UIElement.ManipulationStarting>.  
  
     L'événement <xref:System.Windows.UIElement.ManipulationStarting> se produit lorsque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] détecte que cette entrée tactile commence à manipuler un objet.  Le code spécifie que la position de la manipulation doit être relative à la <xref:System.Windows.Window> en définissant la propriété <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  Dans la classe `MainWindow`, ajoutez le gestionnaire d'événements <xref:System.Windows.Input.ManipulationDelta> suivant.  
  
     L'événement <xref:System.Windows.Input.ManipulationDelta> se produit lorsque l'entrée tactile modifie la position et peut avoir lieu plusieurs fois pendant une manipulation.  L'événement peut également se produire après qu'un doigt soit enlevé.  Par exemple, si l'utilisateur fait glisser un doigt sur l'écran, l'événement <xref:System.Windows.Input.ManipulationDelta> se produit plusieurs fois au fil du déplacement du doigt.  Lorsque l'utilisateur enlève un doigt de l'écran, l'événement <xref:System.Windows.Input.ManipulationDelta> continue de se produire pour simuler l'inertie.  
  
     Le code applique la <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> au <xref:System.Windows.UIElement.RenderTransform%2A> du <xref:System.Windows.Shapes.Rectangle> pour le déplacer tandis que l'utilisateur déplace l'entrée tactile.  Il vérifie également si le <xref:System.Windows.Shapes.Rectangle> se situe à l'extérieur des limites de la <xref:System.Windows.Window> lorsque l'événement se produit pendant l'inertie.  Le cas échéant, l'application appelle la méthode <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=fullName> pour terminer la manipulation.  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  Dans la classe `MainWindow`, ajoutez le gestionnaire d'événements <xref:System.Windows.UIElement.ManipulationInertiaStarting> suivant.  
  
     L'événement <xref:System.Windows.UIElement.ManipulationInertiaStarting> se produit lorsque l'utilisateur enlève tous les doigts de l'écran.  Le code définit la rapidité initiale et la décélération pour le déplacement, l'expansion et la rotation du rectangle.  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  Générez et exécutez le projet.  
  
     Vous devez voir un carré rouge apparaître dans la fenêtre.  
  
## Test de l'application  
 Pour tester l'application, essayez les manipulations suivantes.  Notez que vous pouvez reproduire plusieurs des manipulations suivantes de manière simultanée.  
  
-   Pour déplacer le <xref:System.Windows.Shapes.Rectangle>, mettez un doigt sur le <xref:System.Windows.Shapes.Rectangle> et déplacez le doigt au travers de l'écran.  
  
-   Pour redimensionner le <xref:System.Windows.Shapes.Rectangle>, mettez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et déplacez ensemble les doigts l'un vers l'autre, ou en les éloignant l'un de l'autre.  
  
-   Pour faire pivoter le <xref:System.Windows.Shapes.Rectangle>, mettez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et faites les pivoter l'un autour de l'autre.  
  
 Pour provoquer l'inertie, enlevez rapidement vos doigts de l'écran lorsque vous exécutez les manipulations précédentes.  Le déplacement, le redimensionnement ou la rotation du <xref:System.Windows.Shapes.Rectangle> auront lieu pendant encore  quelques secondes avant de s'arrêter.  
  
## Voir aussi  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=fullName>