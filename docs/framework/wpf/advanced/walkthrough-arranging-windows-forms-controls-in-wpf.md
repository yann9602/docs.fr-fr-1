---
title: "Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les Windows Forms dans WPF | Microsoft Docs"
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
  - "réorganiser les contrôles"
  - "applications hybrides (interopérabilité WPF)"
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les Windows Forms dans WPF
Cette procédure pas à pas indique comment utiliser les fonctionnalités de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour réorganiser des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans une application hybride.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   création du projet ;  
  
-   Utilisation des paramètres de présentation par défaut.  
  
-   Dimensionnement relatif au contenu.  
  
-   Utilisation de positions absolues.  
  
-   Spécification explicite de la taille.  
  
-   Définition des propriétés de présentation.  
  
-   Présentation des limitations dans l'ordre de plan.  
  
-   Ancrage.  
  
-   Définition de la visibilité.  
  
-   Hébergement d'un contrôle qui ne s'étire pas.  
  
-   Mise à l'échelle.  
  
-   Rotation.  
  
-   Définition de marge intérieure et de marges.  
  
-   Utilisation de conteneurs de présentation dynamiques.  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [Disposition de contrôles Windows Forms dans Windows Presentation Foundation, exemple](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Lorsque vous avez terminé, vous disposez de connaissances relatives aux fonctionnalités de présentation [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Création du projet  
  
#### Pour créer et paramétrer le projet  
  
1.  Créez un projet Application WPF nommé `WpfLayoutHostingWf`.  
  
2.  Dans l'Explorateur de solutions, ajoutez une référence aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Double\-cliquez sur MainWindow.xaml pour l'ouvrir dans la vue XAML.  
  
4.  Dans l'élément <xref:System.Windows.Window>, ajoutez le mappage d'espaces de noms [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] suivant.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Dans l'élément <xref:System.Windows.Controls.Grid>, attribuez la valeur `true` à la propriété <xref:System.Windows.Controls.Grid.ShowGridLines%2A> et définissez cinq lignes et trois colonnes.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## Utilisation des paramètres de présentation par défaut  
 Par défaut, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> gère la présentation du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé.  
  
#### Pour utiliser les paramètres de présentation par défaut  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=fullName> apparaît dans le <xref:System.Windows.Controls.Canvas>.  Le contrôle hébergé est dimensionné selon son contenu et l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est dimensionné selon le contrôle hébergé.  
  
## Dimensionnement relatif au contenu  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> s'assure que le contrôle hébergé est dimensionné pour afficher correctement son contenu.  
  
#### Pour dimensionner selon le contenu  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Les deux nouveaux contrôles bouton sont dimensionnés pour afficher la chaîne de texte la plus longue et la taille de police la plus grande, et les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont redimensionnés pour contenir les contrôles hébergés.  
  
## Utilisation de positions absolues  
 Vous pouvez utiliser les positions absolues pour placer l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n'importe où dans l'interface utilisateur.  
  
#### Pour utiliser des positions absolues  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est positionné à 20 pixels du haut de la cellule de grille et à 20 pixels en partant de la gauche.  
  
## Spécification explicite de la taille  
 Vous pouvez spécifier la taille de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> en utilisant les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.  
  
#### Pour spécifier explicitement la taille  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> a une taille de 50 pixels en largeur et de 70 pixels en hauteur, qui est inférieure aux paramètres de présentation par défaut.  Le contenu du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réorganisé en conséquence.  
  
## Définition des propriétés de présentation  
 Définissez toujours les propriétés de présentation sur le contrôle hébergé en utilisant les propriétés de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Si vous définissez les propriétés de présentation directement sur le contrôle hébergé, vous obtiendrez des résultats inattendus.  
  
 La définition des propriétés de présentation sur le contrôle hébergé en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est sans effet.  
  
#### Pour afficher les effets de la définition des propriétés sur le contrôle hébergé  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  Dans l'Explorateur de solutions, double\-cliquez sur MainWindow.xaml.  vb ou MainWindow.xaml.cs pour l'ouvrir dans l'Éditeur de code.  
  
3.  Copiez le code suivant dans la définition de classe `MainWindow`.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Appuyez sur F5 pour générer et exécuter l'application.  
  
5.  Cliquez sur le bouton **Cliquez sur moi**.  Le gestionnaire d'événements `button1_Click` définit les propriétés <xref:System.Windows.Forms.Control.Top%2A> et <xref:System.Windows.Forms.Control.Left%2A> sur le contrôle hébergé.  Le contrôle hébergé est ainsi repositionné dans l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  L'hôte conserve la même zone d'écran, mais le contrôle hébergé est découpé.  À la place, le contrôle hébergé doit toujours remplir l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
## Présentation des limitations dans l'ordre de plan  
 Par défaut, les éléments visibles d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont toujours dessinés sur d'autres éléments de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , et ils ne sont pas affectés par l'ordre de plan.  Pour activer z\-classer, affectez à la propriété d' <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> la valeur true et la propriété d' <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> à <xref:System.Windows.Interop.CompositionMode.Full> ou à <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### Pour voir le comportement par défaut de l'ordre de plan  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément  <xref:System.Windows.Forms.Integration.WindowsFormsHost> est peint sur l'élément label.  
  
#### Pour voir le comportement de l'ordre de plan lorsque IsRedirected a la valeur true  
  
1.  Remplacez l'exemple précédent d'ordre de plan par le code XAML suivant.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     Appuyez sur F5 pour générer et exécuter l'application.  L'élément label est peint sur l'élément d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> .  
  
## Ancrage  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> prend en charge l'ancrage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Définissez la propriété attachée <xref:System.Windows.Controls.DockPanel.Dock%2A> pour ancrer le contrôle hébergé dans un élément <xref:System.Windows.Controls.DockPanel>.  
  
#### Pour ancrer un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est ancré à droite de l'élément <xref:System.Windows.Controls.DockPanel>.  
  
## Définition de la visibilité  
 Vous pouvez faire en sorte que le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] soit invisible ou réduit en définissant la propriété <xref:System.Windows.UIElement.Visibility%2A> sur l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Lorsqu'un contrôle est invisible, il n'est pas affiché, mais il occupe l'espace de présentation.  Lorsqu'un contrôle est réduit, il n'est pas affiché, et n'occupe pas l'espace de présentation.  
  
#### Pour définir la visibilité d'un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Cliquez sur le bouton **Cliquer pour rendre invisible** pour rendre l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> invisible.  
  
5.  Cliquez sur le bouton **Cliquer pour réduire** pour masquer l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> entièrement dans la présentation.  Lorsque le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réduit, les éléments voisins sont réorganisés pour occuper son espace.  
  
## Hébergement d'un contrôle qui ne s'étire pas  
 Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ont une taille fixe et ne s'étirent pas pour remplir l'espace disponible dans la présentation.  Par exemple, le contrôle <xref:System.Windows.Forms.MonthCalendar> affiche un mois dans un espace fixe.  
  
#### Pour héberger un contrôle qui ne s'étire pas  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> sur la ligne de la grille, mais il n'est pas étiré pour remplir l'espace disponible.  Si la fenêtre est suffisamment grande, deux mois ou plus peuvent être affichés par le contrôle <xref:System.Windows.Forms.MonthCalendar> hébergés, mais ils sont centrés sur la ligne.  Le moteur de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] centre les éléments qui ne peuvent pas être dimensionnés de façon à remplir l'espace disponible.  
  
## Mise à l'échelle  
 Contrairement aux éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la plupart des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne sont pas mis à l'échelle en continu.  par défaut, l'élément d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> met à l'échelle son contrôle hébergé si possible.  Pour activer la véritable mise à l'échelle, affectez à la propriété d' <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> la valeur true et la propriété d' <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> à <xref:System.Windows.Interop.CompositionMode.Full> ou à <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### Pour mettre à l'échelle un contrôle hébergé à l'aide de le comportement par défaut  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Le contrôle hébergé et ses éléments avoisinants sont mis à l'échelle en respectant un facteur de 0,5.  Toutefois, la police du contrôle hébergé n'est pas mise à l'échelle.  
  
#### Pour mettre à l'échelle un contrôle hébergé en définissant IsRedirected true  
  
1.  Remplacez l'exemple précédent de mise à l'échelle par le code XAML suivant.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Le contrôle hébergé, ses éléments voisins, et la police du contrôle hébergé sont mis à l'échelle par un facteur 0,5.  
  
## Rotation  
 Contrairement aux éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la rotation.  Par défaut, l'élément d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> ne pivotent pas avec d'autres éléments de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lorsqu'une transformation de rotation est appliquée.  Les valeurs de rotation autres que 180 degrés déclenchent l'événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.  Pour activer la rotation à tout angle, affectez à la propriété d' <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> d' <xref:System.Windows.Forms.Integration.WindowsFormsHost> la valeur true et la propriété d' <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> à <xref:System.Windows.Interop.CompositionMode.Full> ou à <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### Pour afficher les effets de la rotation dans une application hybride  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Le contrôle hébergé ne pivote pas, mais ses éléments voisins subissent une rotation de 180 degrés.  Vous devrez peut\-être redimensionner la fenêtre pour apercevoir les éléments.  
  
#### Pour afficher les effets de la rotation dans une application hybride lorsque IsRedirected a la valeur true  
  
1.  Remplacez l'exemple précédent de rotation par le code XAML suivant.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Le contrôle hébergé est pivoté.  Notez que la propriété d' <xref:System.Windows.Media.RotateTransform.Angle%2A> peut être définie sur une valeur.  Vous devrez peut\-être redimensionner la fenêtre pour apercevoir les éléments.  
  
## Définition de marge intérieure et de marges  
 Les marge intérieure et marges dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont semblables aux marge intérieure et marges dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Il suffit de définir les propriétés <xref:System.Windows.Controls.Control.Padding%2A> et <xref:System.Windows.FrameworkElement.Margin%2A> sur l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
#### Pour définir la marge intérieure et les marges d'un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  Les paramètres de marge intérieure et de marges sont appliqués aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés de la même façon qu'ils seraient appliqués dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## Utilisation de conteneurs de présentation dynamiques  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] fournis deux conteneurs de présentation dynamiques, <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel>.  Vous pouvez aussi utiliser ces conteneurs dans des présentations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
#### Pour utiliser un conteneur de présentation dynamique  
  
1.  Copiez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Ajoutez un appel à la méthode `InitializeFlowLayoutPanel` dans le constructeur.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Appuyez sur F5 pour générer et exécuter l'application.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> remplit le <xref:System.Windows.Controls.DockPanel>, et le <xref:System.Windows.Forms.FlowLayoutPanel> réorganise ses contrôles enfants dans le <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> par défaut.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Considérations sur la disposition de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [Réorganisation des contrôles Windows Forms dans le WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)