---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite WPF dans les Windows Forms | Microsoft Docs"
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
  - "héberger un contenu WPF dans les Windows Forms"
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite WPF dans les Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un environnement riche pour créer des applications.  Toutefois, lorsque vous avez un investissement substantiel dans le code [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], il peut être plus efficace d'étendre votre application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] existante avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plutôt que la réécrire à partir de zéro.  Un scénario courant consiste à incorporer un ou plusieurs contrôles implémentés avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans votre application [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Pour plus d'informations sur la personnalisation des contrôles WPF, consultez [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md).  
  
 Cette procédure pas à pas décrit l'hébergement d'un contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par une application, en vue d'effectuer une saisie de données dans une application [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  Le contrôle composite est empaqueté dans une DLL.  Cette procédure générale peut être étendue à des applications et des contrôles plus complexes.  Cette procédure pas à pas a été conçue pour être quasiment identique, au niveau de l'apparence et des fonctionnalités, à [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md).  La différence principale est que le scénario d'hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections.  La première section décrit brièvement l'implémentation du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La deuxième section explique en détail comment héberger le contrôle composite dans une application [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)], recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Implémentation du contrôle composite WPF.  
  
-   Implémentation de l'application hôte Windows Forms.  
  
 Pour obtenir l'intégralité du code de toutes les tâches illustrées dans cette procédure pas à pas, consultez [Hébergement d'un contrôle composite Windows Presentation Foundation dans les Windows Forms, exemple](http://go.microsoft.com/fwlink/?LinkID=159996).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Implémentation du contrôle composite WPF  
 Le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisé dans cet exemple est un formulaire de saisie de données simple qui prend le nom et l'adresse de l'utilisateur.  Lorsque l'utilisateur clique sur l'un des deux boutons pour indiquer que la tâche est terminée, le contrôle déclenche un événement personnalisé pour retourner cette information à l'hôte.  L'illustration suivante montre le contrôle rendu.  
  
 ![Contrôle WPF simple](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
Contrôle composite WPF  
  
### Création du projet  
 Pour commencer le projet :  
  
1.  Lancez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et ouvrez la boîte de dialogue **Nouveau projet**.  
  
2.  En Visual C\#, sous la catégorie Windows, sélectionnez le modèle **Bibliothèque de contrôles utilisateur WPF**.  
  
3.  Nommez le nouveau projet `MyControls`.  
  
4.  Pour l'emplacement, spécifiez un dossier de niveau supérieur dont le nom est explicite, tel que `WindowsFormsHostingWpfControl`.  Ultérieurement, vous placerez l'application hôte dans ce dossier.  
  
5.  Cliquez sur **OK** pour créer le projet.  Le projet par défaut contient un contrôle unique nommé `UserControl1`.  
  
6.  Dans l'Explorateur de solutions, renommez `UserControl1` en `MyControl1`.  
  
 Votre projet doit avoir des références aux DLL système suivantes.  Si l'une de ces DLL n'est pas incluse par défaut, ajoutez\-la à votre projet.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Système  
  
-   WindowsBase  
  
### Création de l'interface utilisateur  
 L'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du contrôle composite est implémentée avec [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Le contrôle composite [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se compose de cinq éléments <xref:System.Windows.Controls.TextBox>.  Chaque élément <xref:System.Windows.Controls.TextBox> a un élément <xref:System.Windows.Controls.TextBlock> associé qui sert d'étiquette.  Deux éléments <xref:System.Windows.Controls.Button> sont présents, qui sont **OK** et **Annuler**.  Lorsque l'utilisateur clique sur un bouton, le contrôle déclenche un événement personnalisé pour retourner les informations à l'hôte.  
  
#### Disposition de base  
 Plusieurs éléments de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sont contenus dans un élément <xref:System.Windows.Controls.Grid>.  Vous pouvez utiliser <xref:System.Windows.Controls.Grid> pour réorganiser le contenu du contrôle composite de la même façon que vous utiliseriez un élément `Table` en HTML.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend également un élément <xref:System.Windows.Documents.Table>, mais <xref:System.Windows.Controls.Grid> est plus léger et convient mieux pour les tâches de disposition simples.  
  
 Le code XAML suivant montre une mise en page de base.  Ce code XAML définit la structure globale du contrôle en spécifiant le nombre de colonnes et de lignes dans l'élément <xref:System.Windows.Controls.Grid>.  
  
 Dans MyControl1.xaml, remplacez le code XAML existant par celui\-ci :  
  
 [!code-xml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### Ajout d'éléments TextBlock et TextBox à la grille  
 Vous placez un élément de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la grille en définissant les attributs <xref:System.Windows.Controls.Grid.RowProperty> et <xref:System.Windows.Controls.Grid.ColumnProperty> de l'élément sur la ligne et dans la colonne appropriées.  Souvenez\-vous que la numérotation de la ligne et de la colonne est de base zéro.  Vous pouvez avoir un élément qui couvre plusieurs colonnes en définissant son attribut <xref:System.Windows.Controls.Grid.ColumnSpanProperty>.  Pour plus d'informations sur les éléments <xref:System.Windows.Controls.Grid>, consultez [Créer un élément de grille](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md).  
  
 Le code XAML suivant montre les éléments <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.TextBlock> du contrôle composite, avec leurs attributs <xref:System.Windows.Controls.Grid.RowProperty> et <xref:System.Windows.Controls.Grid.ColumnProperty>, configurés pour placer correctement les éléments dans la grille.  
  
 Dans MyControl1.xaml, ajoutez le code XAML suivant dans l'élément <xref:System.Windows.Controls.Grid>.  
  
 [!code-xml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### Application de style aux éléments de l'interface utilisateur  
 Nombre d'éléments du formulaire de saisie de données ont une apparence semblable, ce qui signifie qu'ils ont des paramètres identiques pour plusieurs de leurs propriétés.  Plutôt que définir séparément les attributs de chaque élément, le code XAML précédent utilise des éléments <xref:System.Windows.Style> pour définir des paramètres de propriété standard pour les classes d'éléments.  Cette approche réduit la complexité du contrôle et vous permet de modifier l'apparence de plusieurs éléments à l'aide d'un même attribut de style.  
  
 Les éléments <xref:System.Windows.Style> sont contenus dans la propriété <xref:System.Windows.FrameworkElement.Resources%2A> de l'élément <xref:System.Windows.Controls.Grid>, de façon à pouvoir être utilisés par tous les éléments du contrôle.  Si un style est nommé, vous l'appliquez à un élément en ajoutant un élément <xref:System.Windows.Style> défini au nom du style.  Les styles qui ne sont pas nommés deviennent le style par défaut de l'élément.  Pour plus d'informations sur les styles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Le code XAML suivant indique les éléments <xref:System.Windows.Style> du contrôle composite.  Pour voir comment les styles sont appliqués aux éléments, consultez le code XAML précédent.  Par exemple, le dernier élément <xref:System.Windows.Controls.TextBlock> a le style `inlineText`, et le dernier élément <xref:System.Windows.Controls.TextBox> utilise le style par défaut.  
  
 Dans MyControl1.xaml, ajoutez le code XAML suivant immédiatement après l'élément de début <xref:System.Windows.Controls.Grid>.  
  
 [!code-xml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### Ajout des boutons OK et Annuler  
 Les derniers éléments du contrôle composite sont les éléments <xref:System.Windows.Controls.Button> **OK** et **Annuler**, qui occupent les deux premières colonnes de la dernière ligne du <xref:System.Windows.Controls.Grid>.  Ces éléments utilisent un gestionnaire d'événements commun, `ButtonClicked`, et le style <xref:System.Windows.Controls.Button> par défaut défini dans le code XAML précédent.  
  
 Dans MyControl1.xaml, ajoutez le code XAML suivant après le dernier élément <xref:System.Windows.Controls.TextBox>.  La partie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du contrôle composite est désormais terminée.  
  
 [!code-xml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### Implémentation du fichier code\-behind  
 Le fichier code\-behind MyControl1.xaml.cs implémente trois tâches essentielles :  
  
1.  Gère l'événement qui se produit lorsque l'utilisateur clique sur l'un des boutons.  
  
2.  Récupère les données des éléments <xref:System.Windows.Controls.TextBox>, et les empaquette dans un objet d'argument d'événement personnalisé.  
  
3.  Déclenche l'événement `OnButtonClick` personnalisé, qui notifie l'hôte que l'utilisateur a fini et renvoie les données à l'hôte.  
  
 Le contrôle expose également plusieurs propriétés de couleur et de police permettant de modifier l'apparence.  Contrairement à la classe <xref:System.Windows.Forms.Integration.WindowsFormsHost>, utilisée pour héberger un contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)], la classe <xref:System.Windows.Forms.Integration.ElementHost> expose uniquement la propriété <xref:System.Windows.Controls.Panel.Background%2A> du contrôle.  Pour maintenir la ressemblance entre cet exemple de code et l'exemple décrit dans [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), le contrôle expose directement les propriétés restantes.  
  
#### Structure de base du fichier code\-behind  
 Le fichier code\-behind se compose d'un espace de noms unique, `MyControls`, qui contiendra deux classes, `MyControl1` et `MyControlEventArgs`.  
  
```  
  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
  
```  
  
 La première classe, `MyControl1`, est une classe partielle qui contient le code qui implémente les fonctionnalités de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] définie dans MyControl1.xaml.  Lorsque MyControl1.xaml est analysé, le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est converti en la même classe partielle, et les deux classes partielles sont fusionnées pour former le contrôle compilé.  Pour cette raison, le nom de la classe dans le fichier code\-behind doit correspondre au nom de la classe assigné à MyControl1.xaml, et il doit hériter de l'élément racine du contrôle.  La deuxième classe, `MyControlEventArgs`, est une classe d'arguments d'événement utilisée pour renvoyer les données à l'hôte.  
  
 Ouvrez MyControl1.xaml.cs.  Modifiez la déclaration de classe existante afin qu'elle porte le nom suivant et hérite de <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### Initialisation du contrôle  
 Le code suivant implémente plusieurs tâches de base :  
  
-   Déclare un événement privé, `OnButtonClick` et son délégué associé, `MyControlEventHandler`.  
  
-   Crée plusieurs variables globales privées qui stockent les données de l'utilisateur.  Ces données sont exposées à l'aide des propriétés correspondantes.  
  
-   Implémente le gestionnaire `Init` pour l'événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle.  Ce gestionnaire initialise les variables globales en leur assignant les valeurs définies dans MyControl1.xaml.  Pour ce faire, il utilise le <xref:System.Windows.FrameworkElement.Name%2A> assigné à un élément <xref:System.Windows.Controls.TextBlock> typique, `nameLabel`, pour accéder aux paramètres de propriété de cet élément.  
  
 Supprimez le constructeur existant et ajoutez le code suivant à votre classe `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### Gestion des événements Click des boutons  
 L'utilisateur indique que la tâche de saisie de données est terminée en cliquant sur le bouton **OK** ou le bouton **Annuler**.  Les deux boutons utilisent le même gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, `ButtonClicked`.  Les deux boutons ont un nom, `btnOK` ou `btnCancel`, qui permet au gestionnaire de déterminer quel bouton a été utilisé en examinant la valeur de l'argument `sender`.  Le gestionnaire effectue les opérations suivantes :  
  
-   Crée un objet `MyControlEventArgs` qui contient les données des éléments <xref:System.Windows.Controls.TextBox>.  
  
-   Si l'utilisateur a cliqué sur le bouton **Annuler**, affecte `false` à la propriété `IsOK` de l'objet `MyControlEventArgs`.  
  
-   Déclenche l'événement `OnButtonClick` pour indiquer à l'hôte que l'utilisateur a fini, et passe à nouveau les données recueillies.  
  
 Ajoutez le code suivant à votre classe `MyControl1`, après la méthode `Init` :  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### Création de propriétés  
 Le reste de la classe expose simplement les propriétés qui correspondent aux variables globales décrites précédemment.  Lorsqu'une propriété change, l'accesseur set modifie l'apparence du contrôle en modifiant les propriétés des éléments correspondantes et en mettant à jour les variables globales sous\-jacentes.  
  
 Ajoutez le code suivant à votre classe `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### Renvoi de données à l'hôte  
 Le dernier composant dans le fichier est la classe `MyControlEventArgs`, utilisée pour renvoyer les données recueillies à l'hôte.  
  
 Ajoutez le code suivant à votre espace de noms `MyControls`.  L'implémentation est simple et n'est pas décrite ultérieurement.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Générez la solution.  La génération produira une DLL nommée MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## Implémentation de l'application hôte Windows Forms  
 L'application hôte [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] utilise un objet <xref:System.Windows.Forms.Integration.ElementHost> pour héberger le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'application gère l'événement `OnButtonClick` pour recevoir les données du contrôle composite.  L'application a également un jeu de cases d'option que vous pouvez utiliser pour modifier l'apparence du contrôle.  L'illustration suivante montre l'application.  
  
 ![Contrôle Avalon d'hébergement Windows Forms](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
Contrôle composite WPF hébergé dans une application Windows Forms  
  
### Création du projet  
 Pour commencer le projet :  
  
1.  Lancez [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] et ouvrez la boîte de dialogue **Nouveau projet**.  
  
2.  En Visual C\#, sous la catégorie Windows, sélectionnez le modèle **Application Windows Forms**.  
  
3.  Nommez le nouveau projet `WFHost`.  
  
4.  Pour l'emplacement, spécifiez le même dossier de niveau supérieur qui contient le projet MyControls.  
  
5.  Cliquez sur **OK** pour créer le projet.  
  
 Vous devez également ajouter une référence à la DLL qui contient `MyControl1` et d'autres assemblys.  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter une référence**.  
  
2.  Cliquez sur l'onglet **Parcourir** et accédez au dossier qui contient MyControls.dll.  Pour cette procédure pas à pas, il s'agit du dossier MyControls\\bin\\Debug.  
  
3.  Sélectionnez MyControls.dll, puis cliquez sur **OK**.  
  
4.  Ajoutez des références aux assemblys suivants.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### Implémentation de l'interface utilisateur de l'application  
 L'interface utilisateur de l'application Windows Forms contient plusieurs contrôles permettant d'interagir avec le contrôle composite WPF.  
  
1.  Dans le Concepteur Windows Forms, ouvrez Form1.  
  
2.  Agrandissez le formulaire pour afficher tous les contrôles.  
  
3.  Dans le coin supérieur droit du formulaire, ajoutez un contrôle <xref:System.Windows.Forms.Panel?displayProperty=fullName> pour contenir le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
4.  Ajoutez les contrôles <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> suivants au formulaire :  
  
    |Nom|Texte|  
    |---------|-----------|  
    |groupBox1|Couleur d'arrière\-plan|  
    |groupBox2|Couleur de premier plan|  
    |groupBox3|Font Size|  
    |groupBox4|Famille de polices|  
    |groupBox5|Style|  
    |groupBox6|Épaisseur de police|  
    |groupBox7|Données de contrôle|  
  
5.  Ajoutez les contrôles <xref:System.Windows.Forms.RadioButton?displayProperty=fullName> suivants aux contrôles <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> :  
  
    |GroupBox|Nom|Texte|  
    |--------------|---------|-----------|  
    |groupBox1|radioBackgroundOriginal|D'origine|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|D'origine|  
    |groupBox2|radioForegroundRed|Rouge|  
    |groupBox2|radioForegroundYellow|Yellow|  
    |groupBox3|radioSizeOriginal|D'origine|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|D'origine|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|Italique|  
    |groupBox6|radioWeightOriginal|D'origine|  
    |groupBox6|radioWeightBold|Bold|  
  
6.  Ajoutez les contrôles <xref:System.Windows.Forms.Label?displayProperty=fullName> suivants au dernier <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> :  Ces contrôles affichent les données retournées par le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    |GroupBox|Nom|Texte|  
    |--------------|---------|-----------|  
    |groupBox7|lblName|Nom :|  
    |groupBox7|lblAddress|Adresse :|  
    |groupBox7|lblCity|Ville :|  
    |groupBox7|lblState|État :|  
    |groupBox7|lblZip|Code postal :|  
  
### Initialisation du formulaire  
 Vous implémentez généralement le code d'hébergement dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> du formulaire.  Le code suivant montre le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>, qui est un gestionnaire pour l'événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que des instructions pour plusieurs variables globales qui seront utilisées ultérieurement.  
  
 Dans le Concepteur Windows Forms, double\-cliquez sur le formulaire pour créer un gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  En haut de Form1.cs, ajoutez les instructions `using` suivantes :  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Remplacez le contenu de la classe `Form1` existante par le code ci\-dessous.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 La méthode `Form1_Load` dans le code précédent affiche la procédure générale pour héberger un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
1.  Créez un nouvel objet <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2.  Affectez <xref:System.Windows.Forms.DockStyle?displayProperty=fullName> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle.  
  
3.  Ajoutez le contrôle <xref:System.Windows.Forms.Integration.ElementHost> à la collection <xref:System.Windows.Forms.Control.Controls%2A> du contrôle <xref:System.Windows.Forms.Panel>.  
  
4.  Créez une instance du contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
5.  Hébergez le contrôle composite en l'assignant à la propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
 Les deux lignes restantes dans la méthode `Form1_Load` associent les gestionnaires à deux événements de contrôle :  
  
-   `OnButtonClick` est un événement personnalisé déclenché par le contrôle composite lorsque l'utilisateur clique sur le bouton **OK** ou **Annuler**.  Vous gérez l'événement pour obtenir la réponse de l'utilisateur et rassembler toutes les données spécifiées par l'utilisateur.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> est un événement standard déclenché par un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lorsqu'il est entièrement chargé.  L'événement est utilisé ici parce que l'exemple doit initialiser plusieurs variables globales à l'aide de propriétés du contrôle.  Lorsque l'événement <xref:System.Windows.Forms.Form.Load> du formulaire se produit, le contrôle n'est pas chargé pleinement et ces valeurs sont encore `null`.  Vous devez attendre jusqu'à ce que l'événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle se produise avant de pouvoir accéder à ces propriétés.  
  
 Le gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> est affiché dans le code précédent.  Le gestionnaire `OnButtonClick` est présenté dans la section suivante.  
  
### Gestion d'OnButtonClick  
 L'événement `OnButtonClick` se produit lorsque l'utilisateur clique sur le bouton **OK** ou **Annuler**.  
  
 Le gestionnaire d'événements vérifie le champ `IsOK` de l'argument d'événement pour déterminer quel bouton a été utilisé.  Les variables de *données* `lbl` correspondent aux contrôles <xref:System.Windows.Forms.Label> décrits précédemment.  Si l'utilisateur clique sur le bouton **OK**, les données des contrôles <xref:System.Windows.Controls.TextBox> du contrôle sont assignées au contrôle <xref:System.Windows.Forms.Label> correspondant.  Si l'utilisateur clique sur **Annuler**, les valeurs <xref:System.Windows.Forms.Label.Text%2A> sont définies sur les chaînes par défaut.  
  
 Ajoutez le gestionnaire d'événements de clic de bouton suivant à la classe `Form1` :  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Générez et exécutez l'application.  Ajoutez du texte dans le contrôle composite WPF, puis cliquez sur **OK**.  Texte qui apparaît sur les étiquettes.  À ce stade, le code n'a pas été ajouté pour la gestion des cases d'option.  
  
### Modification de l'apparence du contrôle  
 Les contrôles <xref:System.Windows.Forms.RadioButton> sur le côté gauche du formulaire permettent à l'utilisateur de modifier les couleurs de premier plan et d'arrière\-plan du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que plusieurs propriétés de police.  La couleur d'arrière\-plan est exposée par l'objet <xref:System.Windows.Forms.Integration.ElementHost>.  Les propriétés restantes sont exposées en tant que propriétés personnalisées du contrôle.  
  
 Double\-cliquez sur chaque contrôle <xref:System.Windows.Forms.RadioButton> du formulaire pour créer des gestionnaires d'événements <xref:System.Windows.Forms.RadioButton.CheckedChanged>.  Remplacez les gestionnaires d'événements <xref:System.Windows.Forms.RadioButton.CheckedChanged> par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Générez et exécutez l'application.  Cliquez sur les différentes cases d'option pour visualiser l'effet sur le contrôle composite WPF.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite 3\-D WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)