---
title: "Procédure pas à pas : Ma première application de bureau WPF"
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
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16ed99181f8462e805638b5d3881464b16f21177
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Procédure pas à pas : Ma première application de bureau WPF
Cette procédure pas à pas fournit une introduction au développement d’un [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application qui inclut les éléments qui sont communes à la plupart des [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications : [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage, code-behind, définitions d’application, contrôles, disposition, liaison de données et styles. 
  
 Cette procédure pas à pas vous guide dans le développement d’une simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application en procédant comme suit. 
  
-   Définition [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour concevoir l’apparence de l’application [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. 
  
-   Écriture de code pour générer le comportement de l’application. 
  
-   Création d’une définition d’application pour gérer l’application. 
  
-   Ajout de contrôles et la création de la disposition pour composer l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Création de styles pour créer une apparence cohérente tout au long d’une application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Liaison de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à des données pour remplir le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à partir des données et de conserver les données et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronisé. 
  
 À la fin de la procédure pas à pas, vous aurez créé un autonome [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] qui permet aux utilisateurs de consulter les notes de frais pour certaines personnes. L’application sera composée de plusieurs [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages qui sont hébergées dans une fenêtre de style navigateur. 
  
 L’exemple de code qui est utilisé pour générer cette procédure pas à pas est disponible pour les deux [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] et [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] à [Introduction à la génération d’Applications](http://go.microsoft.com/fwlink/?LinkID=160008). 

## <a name="prerequisites"></a>Prérequis  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)] ou version ultérieure

Pour plus d’informations sur l’installation de la dernière version de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).
  
## <a name="creating-the-application-project"></a>Création du projet d’application  
 Dans cette section, vous allez créer l’infrastructure d’application, qui inclut une définition d’application, deux pages et une image. 
  
1. Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `ExpenseIt`. Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82). 
  
    > [!NOTE]
    >  Cette procédure pas à pas utilise le <xref:System.Windows.Controls.DataGrid> contrôle qui est disponible dans le .NET Framework 4. Être sûr que votre projet cible le .NET Framework 4 ou version ultérieure. Pour plus d’informations, consultez[Comment : cibler une Version du .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
2. Ouvrez Application.xaml (Visual Basic) ou App.xaml (C#). 
  
     Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier définit un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application et toutes les ressources de l’application. Vous utilisez également ce fichier pour spécifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui s’affiche automatiquement lorsque l’application démarre ; dans ce cas, MainWindow.xaml. 
  
     Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     Ou à cela en C# :  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. Ouvrez MainWindow.xaml. 
  
     Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est la fenêtre principale de votre application et affiche le contenu créé dans les pages. La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, telles que son titre, la taille ou icône et gère les événements, tels que la fermeture ou le masquage. 
  
4. Modifier la <xref:System.Windows.Window> élément à un <xref:System.Windows.Navigation.NavigationWindow>. 
  
     Cette application accèdera à différents contenus en fonction de l’interaction de l’utilisateur. Par conséquent, le principal <xref:System.Windows.Window> doit être remplacé par un <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>hérite de toutes les propriétés de <xref:System.Windows.Window>. Le <xref:System.Windows.Navigation.NavigationWindow> élément dans le fichier XAML crée une instance de la <xref:System.Windows.Navigation.NavigationWindow> classe. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md). 
  
5. Modifiez les propriétés suivantes sur le <xref:System.Windows.Navigation.NavigationWindow> élément :  
  
    -   Définir le <xref:System.Windows.Window.Title%2A> propriété « ExpenseIt ». 
  
    -   Définir le <xref:System.Windows.FrameworkElement.Width%2A> propriété 500 pixels. 
  
    -   Définir le <xref:System.Windows.FrameworkElement.Height%2A> propriété à 350 pixels. 
  
    -   Supprimer le <xref:System.Windows.Controls.Grid> éléments entre les <xref:System.Windows.Navigation.NavigationWindow> balises. 
  
     Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     Ou à cela en C# :  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs. 
  
     Ce fichier est un fichier code-behind qui contient le code permettant de gérer les événements déclarés dans MainWindow.xaml. Ce fichier contient une classe partielle pour la fenêtre définie en XAML. 
  
7. Si vous utilisez c#, modifiez le `MainWindow` classe à dériver de <xref:System.Windows.Navigation.NavigationWindow>. 
  
     En Visual Basic, cela se produit automatiquement quand vous modifiez la fenêtre en XAML. 
  
     Votre code doit ressembler à ce qui suit : 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>Ajout de fichiers à l’application  
 Dans cette section, vous allez ajouter deux pages et une image à l’application. 
  
1. Ajouter une nouvelle Page (WPF) au projet nommé `ExpenseItHome.xaml`. Pour plus d’informations, consultez [Comment : ajouter de nouveaux éléments à un projet WPF](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad). 
  
     Cette page est la première page qui s’affiche au lancement de l’application. Elle affiche une liste dans laquelle un utilisateur peut sélectionner une personne pour en afficher les notes de frais. 
  
2. Ouvrez ExpenseItHome.xaml. 
  
3. Définir le <xref:System.Windows.Controls.Page.Title%2A> à « ExpenseIt - Home ». 
  
     Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     Ou à cela en C# :  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. Ouvrez MainWindow.xaml. 
  
5. Définir le <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriété sur le <xref:System.Windows.Navigation.NavigationWindow> à « ExpenseItHome.xaml ». 
  
     ExpenseItHome.xaml est alors la première page ouverte au démarrage de l’application. Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     Ou à cela en C# :  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. Ajouter une nouvelle Page (WPF) au projet nommé `ExpenseReportPage.xaml`. 
  
     Cette page affiche la note de frais de la personne sélectionnée sur ExpenseItHome.xaml. 
  
7. Ouvrez ExpenseReportPage.xaml. 
  
8. Définir le <xref:System.Windows.Controls.Page.Title%2A> à « ExpenseIt - View Expense ». 
  
     Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     Ou à cela en C# :  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. Ouvrez ExpenseItHome.xaml.vb et ExpenseReportPage.xaml.vb, ou ExpenseItHome.xaml.cs et ExpenseReportPage.xaml.cs. 
  
     Lorsque vous créez un nouveau fichier Page, Visual Studio crée automatiquement un fichier code-behind. Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur. 
  
     Votre code doit ressembler à ce qui suit : 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. Ajoutez au projet une image nommée watermark.png. Vous pouvez soit créer votre propre image, soit copier le fichier à partir de l’exemple de code. Pour plus d’informations, consultez [NIB : Comment : ajouter des éléments existants à un projet](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3). 

## <a name="building-and-running-the-application"></a>Générer et exécuter l’application  
 Dans cette section, vous allez générer et exécuter l’application. 
  
1. Générer et exécuter l’application en appuyant sur F5 ou sélectionnez **démarrer le débogage** à partir de la **déboguer** menu. 
  
     L’illustration suivante montre l’application avec le <xref:System.Windows.Navigation.NavigationWindow> boutons. 
  
     ![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. Fermez l’application pour revenir à [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. 
  
## <a name="creating-the-layout"></a>Création de la disposition  
 Mise en page offre placer de manière ordonnée [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments et gère également la taille et la position de ces éléments lorsqu’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est redimensionné. En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Chacun de ces contrôles de disposition prend en charge un type spécial de disposition pour ses éléments enfants. Les pages ExpenseIt peuvent être redimensionnées et chaque page comporte des éléments organisés horizontalement et verticalement en même temps que d’autres éléments. Par conséquent, le <xref:System.Windows.Controls.Grid> est l’élément de disposition idéal pour l’application. 
  
> [!NOTE]
>  Pour plus d’informations sur <xref:System.Windows.Controls.Panel> éléments, consultez [vue d’ensemble des panneaux](../../../../docs/framework/wpf/controls/panels-overview.md). Pour plus d’informations sur la mise en page, consultez [disposition](../../../../docs/framework/wpf/advanced/layout.md). 
  
 Dans la section, vous créez une seule colonne de table avec trois lignes et une marge de 10 pixels en ajoutant des définitions de colonne et de ligne à la <xref:System.Windows.Controls.Grid> dans ExpenseItHome.xaml. 
  
1. Ouvrez ExpenseItHome.xaml. 
  
2. Définir le <xref:System.Windows.FrameworkElement.Margin%2A> propriété sur le <xref:System.Windows.Controls.Grid> élément à la valeur « 10,0,10,10 » qui correspond aux marges gauche, haut, droite et bas. 
  
3. Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre les <xref:System.Windows.Controls.Grid> balises pour créer les définitions de ligne et de colonne. 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     Le <xref:System.Windows.Controls.RowDefinition.Height%2A> de deux lignes est définie sur <xref:System.Windows.GridLength.Auto%2A> sur le contenu dans les lignes de base de ce qui signifie que les lignes seront redimensionnées. La valeur par défaut <xref:System.Windows.Controls.RowDefinition.Height%2A> est <xref:System.Windows.GridUnitType.Star> dimensionnement, ce qui signifie que la ligne sera une proportion pondérée de l’espace disponible. Par exemple, si deux lignes ont une hauteur de « * », elles auront chacune une hauteur représentant la moitié de l’espace disponible.  
  
     Votre <xref:System.Windows.Controls.Grid> doit maintenant ressembler au code XAML suivant :  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>Ajout de contrôles  
 Dans cette section, la page d’accueil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est mis à jour pour afficher une liste des personnes que les utilisateurs peuvent sélectionner pour afficher la note de frais pour la personne sélectionnée. Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application. Pour plus d’informations, consultez [Contrôles](../../../../docs/framework/wpf/controls/index.md). 
  
 Pour créer ce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], les éléments suivants sont ajoutés à ExpenseItHome.xaml :  
  
-   <xref:System.Windows.Controls.ListBox>(pour la liste des personnes). 
  
-   <xref:System.Windows.Controls.Label>(pour l’en-tête de liste). 
  
-   <xref:System.Windows.Controls.Button>(pour cliquez pour afficher la note de frais pour la personne qui est sélectionnée dans la liste). 
  
 Chaque contrôle est placé dans une ligne de la <xref:System.Windows.Controls.Grid> en définissant le <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriété jointe. Pour plus d’informations sur les propriétés jointes, consultez [joint la vue d’ensemble des propriétés](../../../../docs/framework/wpf/advanced/attached-properties-overview.md). 
  
1. Ouvrez ExpenseItHome.xaml. 
  
2. Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre les <xref:System.Windows.Controls.Grid> balises. 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. Générez et exécutez l’application. 
  
 L’illustration suivante montre les contrôles créés par le code XAML dans cette section. 
  
 ![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>Ajout d’une image et un titre  
 Dans cette section, la page d’accueil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est mis à jour avec une image et un titre de page. 
  
1. Ouvrez ExpenseItHome.xaml. 
  
2. Ajouter une colonne à la <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixe <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels. 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. Ajouter une autre ligne pour le <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. Déplacer les contrôles vers la deuxième colonne en définissant <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> sur 1. Déplacez chaque contrôle d’une ligne, vers le bas en augmentant la <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> par 1. 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. Définir le <xref:System.Windows.Controls.Panel.Background%2A> de le <xref:System.Windows.Controls.Grid> soit le fichier image watermark.png. 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. Avant du <xref:System.Windows.Controls.Border>, ajoutez un <xref:System.Windows.Controls.Label> avec le contenu « View Expense Report » comme titre de la page. 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. Générez et exécutez l’application. 
  
 L’illustration suivante montre les résultats de cette section. 
  
 ![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>Ajout d’un code pour gérer des événements  
  
1. Ouvrez ExpenseItHome.xaml. 
  
2. Ajouter un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements à la <xref:System.Windows.Controls.Button> élément. Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements Simple](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480). 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. Ouvrez ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs. 
  
4. Ajoutez le code suivant à la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements, ce qui entraîne la fenêtre pour accéder au fichier ExpenseReportPage.xaml. 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>Création de l’interface utilisateur pour ExpenseReportPage  
 ExpenseReportPage.xaml affiche la note de frais correspondant à la personne qui a été sélectionnée dans ExpenseItHome.xaml. Cette section ajoute des contrôles et crée le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour ExpenseReportPage.xaml. Cette section ajoute aussi des couleurs d’arrière-plan et de remplissage vers les différents [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments. 
  
1. Ouvrez ExpenseReportPage.xaml. 
  
2. Ajoutez le XAML suivant entre les balises <xref:System.Windows.Controls.Grid>. 
  
     Cette interface utilisateur est similaire à l’interface utilisateur créée sur ExpenseItHome.xaml, sauf les données du rapport s’affiche dans un <xref:System.Windows.Controls.DataGrid>. 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. Générez et exécutez l’application. 
  
    > [!NOTE]
    >  Si vous obtenez une erreur qui le <xref:System.Windows.Controls.DataGrid> est introuvable ou n’existe pas, assurez-vous que votre projet cible le .NET Framework 4 ou version ultérieur. Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
4. Cliquez sur le **vue** bouton. 
  
     La page de note de frais s’affiche. 
  
 L’illustration suivante montre le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments ajoutés à ExpenseReportPage.xaml. Notez que le bouton de navigation Précédent est activé. 
  
 ![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>Contrôles de styles  
 L’apparence des différents éléments peut souvent être la même pour tous les éléments du même type dans un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] utilise des styles pour pouvoir réutiliser l’apparence sur plusieurs éléments. La réutilisation des styles permet de simplifier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] création et la gestion. Pour plus d’informations sur les styles, consultez [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md). Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes. 
  
1. Ouvrez Application.xaml ou App.xaml. 
  
2. Ajoutez le code XAML suivant entre les <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> balises :  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ajoute les styles suivants :  
  
    -  `headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>. 
  
    -  `labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> . 
  
    -  `columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>. 
  
    -  `listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste. 
  
    -  `listHeaderTextStyle`: Pour mettre en forme l’en-tête de liste <xref:System.Windows.Controls.Label>. 
  
    -  `buttonStyle`: Pour mettre en forme le <xref:System.Windows.Controls.Button> sur ExpenseItHome.xaml. 
  
     Notez que les styles sont des ressources et des enfants de le <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> élément de propriété. À cet emplacement, les styles sont appliqués à tous les éléments d’une application. Pour obtenir un exemple d’utilisation des ressources dans un [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, consultez [utiliser les ressources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md). 
  
3. Ouvrez ExpenseItHome.xaml. 
  
4. Remplacez tout le contenu entre les <xref:System.Windows.Controls.Grid> éléments avec le code XAML suivant. 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles. Par exemple, le `headerTextStyle` est appliqué à la « View Expense Report » <xref:System.Windows.Controls.Label>. 
  
5. Ouvrez ExpenseReportPage.xaml. 
  
6. Remplacez tout le contenu entre les <xref:System.Windows.Controls.Grid> éléments avec le code XAML suivant. 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     Des styles sont ajoutés aux éléments <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Border> . 
  
7. Générez et exécutez l’application. 
  
     Après avoir ajouté le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans cette section, l’application recherche le même comme avant la mise à jour avec les styles. 
  
## <a name="binding-data-to-a-control"></a>Liaison de données à un contrôle  
 Dans cette section, vous créez le [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] données liées à différents contrôles. 
  
1. Ouvrez ExpenseItHome.xaml. 
  
2. Après l’ouverture <xref:System.Windows.Controls.Grid> élément, ajoutez le code XAML suivant pour créer un <xref:System.Windows.Data.XmlDataProvider> qui contient les données pour chaque personne. 
  
     Les données sont créées en tant qu’un <xref:System.Windows.Controls.Grid> ressource. Les données sont normalement chargées en tant que fichier, mais pour des raisons pratiques, elles sont ajoutées inline. 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. Dans le <xref:System.Windows.Controls.Grid> ressource, ajoutez le code suivant <xref:System.Windows.DataTemplate>, qui définit comment afficher les données dans le <xref:System.Windows.Controls.ListBox>. Pour plus d’informations sur les modèles de données, consultez [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md). 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. Remplacer la <xref:System.Windows.Controls.ListBox> avec le code XAML suivant. 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     Ce code XAML lie le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de la <xref:System.Windows.Controls.ListBox> à la source de données et applique le modèle de données en tant que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. 
  
## <a name="connecting-data-to-controls"></a>Connexion de données aux contrôles  
 Dans cette section, vous écrivez le code qui Récupère l’élément actuel est sélectionné dans la liste de personnes sur la page ExpenseItHome.xaml et sa référence au constructeur de `ExpenseReportPage` lors de l’instanciation. `ExpenseReportPage` définit son contexte de données avec l’élément passé, c’est-à-dire l’élément auquel les contrôles définis dans ExpenseReportPage.xaml seront liés. 
  
1. Ouvrez ExpenseReportPage.xaml.vb ou ExpenseReportPage.xaml.cs. 
  
2. Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée. 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. Ouvrez ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs. 
  
4. Modifier la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements pour appeler le constructeur de nouveau en passant les données de rapport de frais de la personne sélectionnée. 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>Conception de styles pour les données avec des modèles de données  
 Dans cette section, vous mettez à jour le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour chaque élément de données lié aux listes à l’aide de modèles de données. 
  
1. Ouvrez ExpenseReportPage.xaml. 
  
2. Lier le contenu de la « Nom » et « Département » <xref:System.Windows.Controls.Label> éléments pour les données appropriées de propriété source. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md). 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. Après l’ouverture <xref:System.Windows.Controls.Grid> élément, ajouter les modèles de données suivants, qui définissent comment afficher les données de rapport de frais.  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. Appliquer les modèles à la <xref:System.Windows.Controls.DataGrid> rapporter des données de colonnes qui affichent la dépense. 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. Générez et exécutez l’application. 
  
6. Sélectionnez une personne, cliquez sur le **vue** bouton. 
  
 L’illustration suivante montre les deux pages de l’application ExpenseIt avec les contrôles, la disposition, les styles, la liaison de données et les modèles de données appliqués. 
  
 ![Exemples de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>meilleures pratiques recommandées.  
 Cet exemple, dont le but est d’illustrer une fonctionnalité spécifique de WPF, ne respecte pas les bonnes pratiques en matière de développement d’applications. Pour une couverture complète de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application meilleures pratiques de développement, consultez les rubriques suivantes comme il convient :  
  
-   Accessibilité - [Meilleures pratiques en matière d’accessibilité](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   Sécurité - [sécurité](../../../../docs/framework/wpf/security-wpf.md)  
  
-   Localisation - [Vue d’ensemble de la globalisation et de la localisation WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   Performances - [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>Quelle est la suite  
 Vous avez maintenant un certain nombre de techniques à votre disposition pour la création d’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’aide de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Vous devez maintenant avoir une bonne connaissance des blocs de construction de base de données liées [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application. Cette rubrique est loin d’être exhaustive, mais j’espère qu’elle vous incitera à découvrir par vous-même d’autres techniques au-delà de celles traitées ici. 
  
 Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :  
  
-   [Architecture de WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [Disposition](../../../../docs/framework/wpf/advanced/layout.md)  
  
 Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :  
  
-   [Développement de l’application](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [Contrôles](../../../../docs/framework/wpf/controls/index.md)  
  
-   [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Génération d’une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Styles et modèles](../../../../docs/framework/wpf/controls/styles-and-templates.md)
