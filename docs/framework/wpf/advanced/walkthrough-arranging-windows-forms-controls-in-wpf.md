---
title: "Procédure pas à pas : organisation des contrôles Windows Forms dans WPF"
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
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67bfa913627d33238aea92acdd49b6d2ecfef2a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Procédure pas à pas : organisation des contrôles Windows Forms dans WPF
Cette procédure pas à pas vous montre comment utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour organiser les fonctionnalités de disposition [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles dans une application hybride.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création du projet  
  
-   Utilisation des paramètres de disposition par défaut  
  
-   Dimensionnement en fonction du contenu  
  
-   Utilisation du positionnement absolu  
  
-   Spécification explicite de la taille  
  
-   Définition des propriétés de disposition  
  
-   Présentation des limitations dans l’ordre de plan  
  
-   Ancrage  
  
-   Définition de la visibilité  
  
-   Hébergement d’un contrôle qui ne s’étire pas  
  
-   Mise à l’échelle  
  
-   Rotation  
  
-   Définition d’une marge intérieure et de marges  
  
-   Utilisation de conteneurs de présentation dynamiques  
  
 Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [organisation des contrôles Windows Forms dans WPF, exemple](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Lorsque vous avez terminé, vous comprendrez de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] des fonctionnalités de disposition dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-en fonction des applications.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet  
  
1.  Créez un projet d’Application WPF nommé `WpfLayoutHostingWf`.  
  
2.  Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Double-cliquez sur MainWindow.xaml pour l’ouvrir dans la vue XAML.  
  
4.  Dans le <xref:System.Windows.Window> élément, ajoutez le code suivant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mappage d’espace de noms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Dans le <xref:System.Windows.Controls.Grid> ensemble d’éléments du <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriété `true` et définissez cinq lignes et trois colonnes.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Utilisation des paramètres de disposition par défaut  
 Par défaut, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément gère la présentation hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.  
  
#### <a name="to-use-default-layout-settings"></a>Pour utiliser les paramètres de disposition par défaut  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> contrôle s’affiche dans le <xref:System.Windows.Controls.Canvas>. Le contrôle hébergé est dimensionné en fonction de son contenu et le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est dimensionné pour prendre en charge le contrôle hébergé.  
  
## <a name="sizing-to-content"></a>Dimensionnement en fonction du contenu  
 Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément garantit que le contrôle hébergé est dimensionné pour afficher correctement son contenu.  
  
#### <a name="to-size-to-content"></a>Pour dimensionner en fonction du contenu  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Les deux nouveaux contrôles bouton sont dimensionnés pour s’afficher correctement, la plus longue chaîne de texte et la taille de police et la <xref:System.Windows.Forms.Integration.WindowsFormsHost> éléments sont redimensionnés pour contenir les contrôles hébergés.  
  
## <a name="using-absolute-positioning"></a>Utilisation du positionnement absolu  
 Vous pouvez utiliser le positionnement absolu pour placer le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément n’importe où dans l’interface utilisateur (IU).  
  
#### <a name="to-use-absolute-positioning"></a>Pour utiliser le positionnement absolu  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> est placé 20 pixels du haut de la cellule de grille et 20 pixels à partir de la gauche.  
  
## <a name="specifying-size-explicitly"></a>Spécification explicite de la taille  
 Vous pouvez spécifier la taille de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> à l’aide de l’élément le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés.  
  
#### <a name="to-specify-size-explicitly"></a>Pour spécifier explicitement la taille  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est défini sur une taille de 50 pixels de large sur 70 pixels de haut, qui est plus petit que les paramètres de disposition par défaut. Le contenu de la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est réorganisé en conséquence.  
  
## <a name="setting-layout-properties"></a>Définition des propriétés de disposition  
 Toujours la valeur relatives à la disposition des propriétés sur le contrôle hébergé en utilisant les propriétés de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément. Si vous définissez les propriétés de disposition directement sur le contrôle hébergé, vous obtiendrez des résultats inattendus.  
  
 Définissant les propriétés de disposition sur le contrôle hébergé dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] n’a aucun effet.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Pour afficher les effets de la définition des propriétés sur le contrôle hébergé  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur MainWindow.xaml. vb ou MainWindow.xaml.cs pour l’ouvrir dans l’éditeur de code.  
  
3.  Copiez le code suivant dans le `MainWindow` définition de classe.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Appuyez sur F5 pour générer et exécuter l'application.  
  
5.  Cliquez sur le **Click me** bouton. Le `button1_Click` Gestionnaire d’événements définit la <xref:System.Windows.Forms.Control.Top%2A> et <xref:System.Windows.Forms.Control.Left%2A> propriétés sur le contrôle hébergé. Le contrôle hébergé est ainsi repositionné dans le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément. L’hôte conserve la même zone d’écran, mais le contrôle hébergé est découpé. Au lieu de cela, le contrôle hébergé doit toujours remplir le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.  
  
## <a name="understanding-z-order-limitations"></a>Présentation des limitations dans l’ordre de plan  
 Par défaut, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> éléments sont dessinées sur les autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments et ils ne sont pas affectés par l’ordre de plan. Pour activer l’ordre de plan, définissez la <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriété de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> sur true et la <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriété <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-default-z-order-behavior"></a>Pour voir le comportement par défaut de l’ordre de plan  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> un élément est dessiné sur l’élément label.  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a>Pour voir le comportement de l’ordre de plan quand IsRedirected a la valeur true  
  
1.  Remplacez l’exemple d’ordre de plan précédent par le code XAML suivant.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     Appuyez sur F5 pour générer et exécuter l'application. L’élément label est peinte sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.  
  
## <a name="docking"></a>Ancrage  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>prend en charge de l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’ancrage. Définir le <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété attachée pour ancrer le contrôle hébergé dans un <xref:System.Windows.Controls.DockPanel> élément.  
  
#### <a name="to-dock-a-hosted-control"></a>Pour ancrer un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est ancré sur le côté droit de la <xref:System.Windows.Controls.DockPanel> élément.  
  
## <a name="setting-visibility"></a>Définition de la visibilité  
 Vous pouvez rendre votre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle invisible ou réduit en définissant le <xref:System.Windows.UIElement.Visibility%2A> propriété sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément. Quand un contrôle est invisible, il n’est pas affiché, mais il occupe l’espace de disposition. Quand un contrôle est réduit, il n’est pas affiché et n’occupe pas l’espace de disposition.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Pour définir la visibilité d’un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Cliquez sur le **cliquez pour rendre invisible** bouton pour rendre le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément invisible.  
  
5.  Cliquez sur le **cliquez pour réduire** bouton permettant de masquer le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément à partir de la mise en page entièrement. Lorsque la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est réduit, les éléments voisins sont réorganisés pour occuper son espace.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Hébergement d’un contrôle qui ne s’étire pas  
 Certains [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles ont une taille fixe et ne prennent pas pour remplir l’espace disponible dans la disposition. Par exemple, le <xref:System.Windows.Forms.MonthCalendar> control affiche un mois dans un espace fixe.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>Pour héberger un contrôle qui ne s’étire pas  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est centré sur la ligne de grille, mais il n’est pas étiré pour remplir l’espace disponible. Si la fenêtre est suffisamment grande, vous pouvez voir deux mois ou plus affichées par hébergé <xref:System.Windows.Forms.MonthCalendar> contrôle, mais ces derniers sont centrés sur la ligne. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du moteur de disposition centre les éléments qui ne peut pas être redimensionnés pour remplir l’espace disponible.  
  
## <a name="scaling"></a>Mise à l'échelle  
 Contrairement aux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments, la plupart des [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] les contrôles ne sont pas évolutifs en permanence. Par défaut, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément met à l’échelle son contrôle hébergé lorsque cela est possible.  Pour activer la mise à l’échelle à part entière, définissez la <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriété de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> sur true et la <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriété <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Pour mettre à l’échelle un contrôle hébergé selon le comportement par défaut  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le contrôle hébergé et ses éléments voisins sont mis à l’échelle par un facteur de 0,5. Toutefois, la police du contrôle hébergé n’est pas mise à l’échelle.  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a>Pour mettre à l’échelle un contrôle hébergé en affectant à IsRedirected la valeur true  
  
1.  Remplacez l’exemple précédent de mise à l’échelle par le code XAML suivant.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le contrôle hébergé, ses éléments voisins et la police du contrôle hébergé sont mis à l’échelle par un facteur 0,5.  
  
## <a name="rotating"></a>Rotation  
 Contrairement aux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles ne prennent pas en charge la rotation. Par défaut, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément ne pivote pas avec d’autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments lors d’une transformation de rotation est appliquée. Les valeurs de rotation autres que 180 degrés déclenche le <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> événement.  Pour activer la rotation à n’importe quel angle, définissez la <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriété de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> sur true et la <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriété <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Pour voir l’effet de la rotation dans une application hybride  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le contrôle hébergé ne pivote pas, mais ses éléments voisins subissent une rotation de 180 degrés. Vous devrez peut-être redimensionner la fenêtre pour apercevoir les éléments.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a>Pour voir l’effet de la rotation dans une application hybride quand IsRedirected a la valeur true  
  
1.  Remplacez l’exemple précédent de rotation par le code XAML suivant.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Le contrôle hébergé est pivoté.  Notez que le <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété peut être définie sur n’importe quelle valeur. Vous devrez peut-être redimensionner la fenêtre pour apercevoir les éléments.  
  
## <a name="setting-padding-and-margins"></a>Définition d’une marge intérieure et de marges  
 Marge intérieure et marges dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont semblables aux marge intérieure et marges dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Il suffit de définir la <xref:System.Windows.Controls.Control.Padding%2A> et <xref:System.Windows.FrameworkElement.Margin%2A> propriétés sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Pour définir la marge intérieure et les marges d’un contrôle hébergé  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Appuyez sur F5 pour générer et exécuter l'application. Les paramètres de marge intérieure et marges sont appliqués à l’élément hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles de la même façon qu’ils peuvent être appliquées dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Utilisation de conteneurs de disposition dynamiques  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]fournit deux conteneurs de disposition dynamique, <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel>. Vous pouvez également utiliser ces conteneurs dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dispositions.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Pour utiliser un conteneur de disposition dynamique  
  
1.  Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> élément.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Ajoutez un appel à la `InitializeFlowLayoutPanel` méthode dans le constructeur.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Appuyez sur F5 pour générer et exécuter l'application. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément remplit la <xref:System.Windows.Controls.DockPanel>, et <xref:System.Windows.Forms.FlowLayoutPanel> réorganise ses contrôles enfants dans la valeur par défaut <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Considérations sur la disposition de l’élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Réorganiser les fenêtres de contrôles Forms dans WPF, exemple](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
