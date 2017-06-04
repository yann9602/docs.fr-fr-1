---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite Windows Forms dans WPF | Microsoft Docs"
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
  - "contrôles composites, héberger dans WPF"
  - "héberger un contrôle Windows Forms dans WPF"
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite Windows Forms dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un environnement riche pour créer des applications.  Toutefois, lorsque vous avez un investissement substantiel dans le code [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plutôt que de la réécrire à partir de zéro.  Le scénario le plus courant se présente lorsque des contrôles [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] existent.  Dans certains cas, vous pouvez même ne pas avoir accès au code source de ces contrôles.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une procédure simple pour l'hébergement de tels contrôles dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Par exemple, vous pouvez utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la plupart de votre programmation tout en hébergeant vos contrôles <xref:System.Windows.Forms.DataGridView> spécialisés.  
  
 Cette procédure pas à pas décrit l'hébergement d'un contrôle composite [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] par une application en vue d'effectuer une saisie des données dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Le contrôle composite est empaqueté dans une DLL.  Cette procédure générale peut être étendue à des applications et des contrôles plus complexes.  Cette procédure pas à pas a été conçue pour être quasiment identique, au niveau de l'apparence et des fonctionnalités, à [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).  La différence principale est que le scénario d'hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections.  La première section décrit brièvement l'implémentation du contrôle composite [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  La deuxième section explique en détail comment héberger le contrôle composite dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Implémentation du contrôle composite Windows Forms.  
  
-   Implémentation de l'application hôte WPF.  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [Hébergement d'un contrôle composite Windows Forms dans Windows Presentation Foundation, exemple](http://go.microsoft.com/fwlink/?LinkID=159999).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Implémentation du contrôle composite Windows Forms  
 Le contrôle composite [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] utilisé dans cet exemple est un formulaire de saisie de données simple.  Ce formulaire prend le nom et l'adresse de l'utilisateur et utilise un événement personnalisé pour retourner ces informations à l'hôte.  L'illustration suivante montre le contrôle rendu.  
  
 ![Contrôle Windows Forms simple](../../../../docs/framework/wpf/advanced/media/wfcontrol.png "WFControl")  
Contrôle composite Windows Forms  
  
### Création du projet  
 Pour commencer le projet :  
  
1.  Lancez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et ouvrez la boîte de dialogue **Nouveau projet**.  
  
2.  Dans la catégorie Fenêtre, sélectionnez le modèle **Bibliothèque de contrôles Windows Forms**.  
  
3.  Nommez le nouveau projet `MyControls`.  
  
4.  Pour l'emplacement, spécifiez un dossier à la racine dont le nom est explicite, tel que `WpfHostingWindowsFormsControl`.  Ultérieurement, vous placerez l'application hôte dans ce dossier.  
  
5.  Cliquez sur **OK** pour créer le projet.  Le projet par défaut contient un contrôle unique nommé `UserControl1`.  
  
6.  Dans l'Explorateur de solutions, renommez `UserControl1` en `MyControl1`.  
  
 Votre projet doit avoir des références aux DLL système suivantes.  Si l'une de ces DLL n'est pas incluse par défaut, ajoutez\-la au projet.  
  
-   Système  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### Ajout de contrôles au formulaire  
 Pour ajouter des contrôles au formulaire :  
  
-   Ouvrez `MyControl1` dans le concepteur.  
  
 Sur le formulaire, ajoutez cinq contrôles <xref:System.Windows.Forms.Label> et leurs contrôles <xref:System.Windows.Forms.TextBox> correspondants, dimensionnés et organisés tels que dans l'illustration précédente.  Dans cet exemple, les contrôles <xref:System.Windows.Forms.TextBox> sont nommés :  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Ajoutez deux contrôles <xref:System.Windows.Forms.Button> étiquetés **OK** et **Annuler**.  Dans cet exemple, les noms de bouton sont `btnOK` et `btnCancel`, respectivement.  
  
### Implémentation du code de prise en charge  
 Ouvrez le formulaire en mode Code.  Le contrôle retourne les données collectées à son hôte en déclenchant l'événement `OnButtonClick` personnalisé.  Les données sont contenues dans l'objet d'argument d'événement.  Le code suivant illustre la déclaration event et delegate.  
  
 Ajoutez le code suivant à la classe `MyControl1`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 La classe `MyControlEventArgs` contient les informations à retourner à l'hôte.  
  
 Ajoutez la classe suivante au formulaire.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 Lorsque l'utilisateur clique sur le bouton **OK** ou **Annuler**, les gestionnaires d'événements <xref:System.Windows.Forms.Control.Click> créent un objet `MyControlEventArgs` qui contient les données et déclenche l'événement `OnButtonClick`.  La seule différence entre les deux gestionnaires est la propriété `IsOK` de l'argument d'événement.  Cette propriété  permet à l'hôte de déterminer le bouton sur lequel l'utilisateur a cliqué.  Elle a la valeur `true` pour le bouton **OK** et la valeur `false` pour le bouton **Annuler**.  Le code suivant illustre les deux gestionnaires de bouton.  
  
 Ajoutez le code suivant à la classe `MyControl1`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### Attribution d'un nom fort à l'assembly et création de l'assembly  
 Pour que cet assembly soit référencé par une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], celui\-ci doit avoir un nom fort.  Pour créer un nom fort, créez un fichier de clé avec Sn.exe et ajoutez\-le à votre projet.  
  
1.  Ouvrez une invite de commandes [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  Pour ce faire, cliquez sur le menu **Démarrer**, puis sélectionnez **Tous les programmes\/Microsoft Visual Studio 2010\/Visual Studio Tools\/Invite de commandes Visual Studio**.  Cette opération lance une fenêtre de console avec des variables d'environnement personnalisées.  
  
2.  À l'invite de commandes, utilisez la commande `cd` pour aller à votre dossier de projet.  
  
3.  Générez un fichier de clé nommé MyControls.snk en exécutant la commande suivante.  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  Pour inclure le fichier de clé dans votre projet, cliquez avec le bouton droit sur le nom de projet dans l'Explorateur de solutions, puis cliquez sur **Propriétés**.  Dans le Concepteur de projets, cliquez sur l'onglet **Signature**, activez la case à cocher **Signer l'assembly**, puis recherchez votre fichier de clé.  
  
5.  Générez la solution.  La génération produira une DLL nommée MyControls.dll.  
  
## Implémentation de l'application hôte WPF  
 L'application hôte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour héberger `MyControl1`.  L'application gère l'événement `OnButtonClick` pour recevoir les données du contrôle.  Elle possède également un ensemble de cases d'option qui vous permettent de modifier certaines propriétés du contrôle à partir de l'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'illustration suivante présente l'application finie.  
  
 ![Contrôle incorporé dans une page WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.png "AvalonHost")  
Application terminée, montrant le contrôle lié dans l'application WPF  
  
### Création du projet  
 Pour commencer le projet :  
  
1.  Ouvrez [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] et sélectionnez **Nouveau projet**.  
  
2.  Dans la catégorie Fenêtre, sélectionnez le modèle **Application WPF**.  
  
3.  Nommez le nouveau projet `WpfHost`.  
  
4.  Pour l'emplacement, spécifiez le même dossier de niveau supérieur qui contient le projet MyControls.  
  
5.  Cliquez sur **OK** pour créer le projet.  
  
 Vous devez également ajouter une référence à la DLL qui contient `MyControl1` et d'autres assemblys.  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter une référence**.  
  
2.  Cliquez sur l'onglet **Parcourir** et accédez au dossier qui contient MyControls.dll.  Pour cette procédure pas à pas, il s'agit du dossier MyControls\\bin\\Debug.  
  
3.  Sélectionnez MyControls.dll, puis cliquez sur **OK**.  
  
4.  Ajoutez une référence à l'assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.  
  
### Implémentation de la disposition de base  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l'application hôte est implémentée dans MainWindow.xaml.  Ce fichier contient du balisage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit la disposition et qui héberge le contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  L'application est divisée en trois zones :  
  
-   Le panneau **Propriétés du contrôle**, qui contient un ensemble de cases d'option que vous pouvez utiliser pour modifier différentes propriétés du contrôle hébergé.  
  
-   Le panneau **Données du contrôle**, qui contient plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé.  
  
-   Le contrôle hébergé lui\-même.  
  
 La disposition de base est indiquée dans le code XAML suivant.  Le balisage qui est nécessaire pour héberger `MyControl1` est omis dans cet exemple mais sera abordé plus tard.  
  
 Remplacez le code XAML dans MainWindow.xaml par les éléments suivants.  Si vous utilisez Visual Basic, modifiez la classe en `x:Class="MainWindow"`.  
  
 [!code-xml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 Le premier élément <xref:System.Windows.Controls.StackPanel> contient plusieurs jeux de contrôles <xref:System.Windows.Controls.RadioButton> qui vous permettent de modifier différentes propriétés par défaut du contrôle hébergé.  Il est suivi par un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, qui héberge `MyControl1`.  L'élément final <xref:System.Windows.Controls.StackPanel> contient plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé.  L'ordre des éléments et les paramètres d'attribut <xref:System.Windows.Controls.DockPanel.Dock%2A> et <xref:System.Windows.FrameworkElement.Height%2A> incorporent le contrôle hébergé sur la fenêtre sans espace ni distorsion.  
  
#### Hébergement du contrôle  
 La version modifiée suivante du code XAML précédent porte sur les éléments nécessaires à l'hébergement de `MyControl1`.  
  
 [!code-xml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 L'attribut de mappage d'espace de noms `xmlns` crée une référence à l'espace de noms `MyControls` qui contient le contrôle hébergé.  Ce mappage vous permet de représenter `MyControl1` en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sous la forme `<mcl:MyControl1>`.  
  
 Deux éléments du code XAML gère l'hébergement :  
  
-   `WindowsFormsHost` représente l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> qui vous permet d'héberger un contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   `mcl:MyControl1`, qui représente `MyControl1`, est ajouté à la collection enfant de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Par conséquent, ce contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] est rendu dans le cadre de la fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et vous pouvez communiquer avec le contrôle à partir de l'application.  
  
### Implémentation du fichier code\-behind  
 Le fichier code\-behind, MainWindow.xaml.vb ou MainWindow.xaml.cs, contient le code procédural qui implémente la fonctionnalité de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] abordée dans la section précédente.  Les tâches principales sont les suivantes :  
  
-   Attachement d'un gestionnaire d'événements à l'événement `OnButtonClick` de `MyControl1`.  
  
-   Modification des différentes propriétés de `MyControl1`, selon la manière dont la collection de cases d'option est définie.  
  
-   Affichage des données collectées par le contrôle.  
  
#### Initialisation de l'application  
 Le code d'initialisation est contenu dans un gestionnaire d'événements pour l'événement <xref:System.Windows.FrameworkElement.Loaded> de la fenêtre et attache un gestionnaire d'événements à l'événement `OnButtonClick` du contrôle.  
  
 Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, ajoutez le code suivant à la classe `MainWindow`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 Compte tenu que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] abordé précédemment a ajouté `MyControl1` à la collection d'éléments enfants de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, vous pouvez effectuer un cast du <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour obtenir la référence à `MyControl1`.  Vous pouvez ensuite utiliser cette référence pour attacher un gestionnaire d'événements à `OnButtonClick`.  
  
 En plus de fournir une référence au contrôle lui\-même, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose plusieurs propriétés du contrôle, que vous pouvez manipuler à partir de l'application.  Le code d'initialisation affecte ces valeurs aux variables globales privées en vue d'une utilisation ultérieure dans l'application.  
  
 Pour que vous puissiez facilement accéder aux types dans la DLL `MyControls`, ajoutez l'instruction `Imports` ou `using` suivante au début du fichier.  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### Gestion de l'événement OnButtonClick  
 `MyControl1` déclenche l'événement `OnButtonClick` lorsque l'utilisateur clique sur l'un des boutons du contrôle.  
  
 Ajoutez le code suivant à la classe `MainWindow`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 Les données des zones de texte sont compressées dans l'objet `MyControlEventArgs`.  Si l'utilisateur clique sur le bouton **OK**, le gestionnaire d'événements extrait les données et les affiche dans le panneau sous `MyControl1`.  
  
#### Modification des propriétés du contrôle  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose plusieurs propriétés par défaut du contrôle hébergé.  Par conséquent, vous pouvez modifier l'apparence du contrôle afin qu'il corresponde davantage au style de votre application.  Les ensembles de cases d'option du panneau de gauche permettent à l'utilisateur de modifier plusieurs propriétés de couleur et de police de caractères.  Chaque ensemble de boutons possède un gestionnaire pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, qui détecte les sélections de cases d'option de l'utilisateur et modifie la propriété correspondante sur le contrôle.  
  
 Ajoutez le code suivant à la classe `MainWindow`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Générez et exécutez l'application.  Ajoutez du texte dans le contrôle composite Windows Forms, puis cliquez sur **OK**.  Texte qui apparaît sur les étiquettes.  Cliquez sur les différentes cases d'option pour visualiser l'effet sur le contrôle.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)