---
title: "Classement par fonction des contr&#244;les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), par fonction"
  - "contrôles Windows Forms, liste de"
  - "Windows Forms, contrôles par fonction"
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Classement par fonction des contr&#244;les Windows Forms
Windows Forms offre des contrôles et des composants qui exécutent plusieurs fonctions.  Le tableau suivant répertorie les contrôles et les composants Windows Forms par fonction générale.  De plus, là où plusieurs contrôles assurant la même fonction existent, le contrôle recommandé est répertorié joint à une note sur le contrôle qu'il a remplacé.  Dans une table suivante distincte, les contrôles remplacés sont répertoriés avec leurs remplacements recommandés.  
  
> [!NOTE]
>  Les tables suivantes ne répertorient pas chaque contrôle ou composant que vous pouvez utiliser dans les Windows Forms. Pour une liste plus complète, consultez [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## Contrôles et composants recommandés par fonction  
  
|Fonction|Contrôle|Description|  
|--------------|--------------|-----------------|  
|Affichage de données|Contrôle <xref:System.Windows.Forms.DataGridView>|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit une table personnalisable pour l'affichage des données.  La classe <xref:System.Windows.Forms.DataGridView> active la personnalisation des cellules, lignes, colonnes et bordures. **Note:**  Le contrôle <xref:System.Windows.Forms.DataGridView> fournit de nombreux éléments de base et des fonctionnalités avancées qui manquent dans le contrôle <xref:System.Windows.Forms.DataGrid>.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).|  
|Liaison de données et navigation|Composant <xref:System.Windows.Forms.BindingSource>|Simplifie la liaison entre les contrôles sur un formulaire et les données en assurant la gestion des devises, la notification des modifications et d'autres services.|  
||Contrôle <xref:System.Windows.Forms.BindingNavigator>|Fournit une interface de type de barre d'outils pour naviguer et manipuler des données sur un formulaire.|  
|Édition de texte|Contrôle <xref:System.Windows.Forms.TextBox>|Affiche un texte entré au moment du design et pouvant être modifié par les utilisateurs au moment de l'exécution ou par programme.|  
||Contrôle <xref:System.Windows.Forms.RichTextBox>|Permet l'affichage du texte au format texte brut ou RTF.|  
||Contrôle <xref:System.Windows.Forms.MaskedTextBox>|Contraint le format d'entrée d'utilisateur|  
|Affichage d'informations \(lecture seule\)|Contrôle <xref:System.Windows.Forms.Label>|Affiche du texte que les utilisateurs ne peuvent pas directement modifier.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d'un lien de style Web et déclenche un événement lorsque l'utilisateur clique sur le texte spécial.  En général, le texte est un lien vers une autre fenêtre ou vers un site Web.|  
||Contrôle <xref:System.Windows.Forms.StatusStrip>|Affiche des informations sur l'état actuel de l'application dans une zone à frame généralement située au bas d'un formulaire parent.|  
||Contrôle <xref:System.Windows.Forms.ProgressBar>|Affiche la progression actuelle d'une opération pour l'utilisateur.|  
|Affichage de page Web|Contrôle <xref:System.Windows.Forms.WebBrowser>|Permet à l'utilisateur de naviguer dans des pages Web à l'intérieur de votre formulaire.|  
|Sélection dans une liste|Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d'éléments accompagnés chacun d'une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.ComboBox>|Affiche une liste déroulante d'éléments.|  
||Contrôle <xref:System.Windows.Forms.DomainUpDown>|Affiche une liste d'éléments que les utilisateurs peuvent faire défiler vers le haut ou le vers le bas à l'aide de boutons.|  
||Contrôle <xref:System.Windows.Forms.ListBox>|Affiche une liste d'éléments texte et graphiques \(icônes\).|  
||Contrôle <xref:System.Windows.Forms.ListView>|Affiche des éléments dans une vue parmi quatre vues différentes.  Les différents types de vue sont : texte seul, texte avec petites icônes, texte avec grandes icônes et détails.|  
||Contrôle <xref:System.Windows.Forms.NumericUpDown>|Affiche une liste de nombres que les utilisateurs peuvent faire défiler vers le haut ou le vers le bas à l'aide de boutons.|  
||Contrôle <xref:System.Windows.Forms.TreeView>|Affiche une collection hiérarchique d'objets nœud qui peut être constituée de texte éventuellement associé à des cases à cocher ou des icônes.|  
|Affichage des graphismes|Contrôle <xref:System.Windows.Forms.PictureBox>|Affiche dans un frame des fichiers graphiques tels qu'images bitmap et icônes.|  
|Stockage des graphismes|Contrôle <xref:System.Windows.Forms.ImageList>|Sert de référentiel d'images.  Les contrôles <xref:System.Windows.Forms.ImageList> et les images qu'ils contiennent peuvent être réutilisés d'une application à l'autre.|  
|Définition de valeurs|Contrôle <xref:System.Windows.Forms.CheckBox>|Affiche une case à cocher et une étiquette pour le texte.  Généralement utilisé pour définir des options.|  
||Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d'éléments accompagnés chacun d'une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.RadioButton>|Affiche une case d'option qui peut être activée ou désactivée.|  
||Contrôle <xref:System.Windows.Forms.TrackBar>|Permet aux utilisateurs de définir des valeurs sur une échelle par le déplacement d'un curseur.|  
|Définition de dates|Contrôle <xref:System.Windows.Forms.DateTimePicker>|Affiche un calendrier graphique permettant aux utilisateurs de sélectionner une date ou une heure.|  
||Contrôle <xref:System.Windows.Forms.MonthCalendar>|Affiche un calendrier graphique permettant aux utilisateurs de sélectionner une plage de dates.|  
|Boîtes de dialogue|Contrôle <xref:System.Windows.Forms.ColorDialog>|Affiche la boîte de dialogue du sélecteur de couleurs qui permet aux utilisateurs de définir la couleur d'un élément d'interface.|  
||Contrôle <xref:System.Windows.Forms.FontDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de définir une police et ses attributs.|  
||Contrôle <xref:System.Windows.Forms.OpenFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de naviguer et de sélectionner un fichier.|  
||Contrôle <xref:System.Windows.Forms.PrintDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de sélectionner une imprimante et de définir ses attributs.|  
||Contrôle <xref:System.Windows.Forms.PrintPreviewDialog>|Affiche une boîte de dialogue qui montre un composant <xref:System.Drawing.Printing.PrintDocument> de contrôle tel qu'il se présentera une fois imprimé.|  
||Contrôle <xref:System.Windows.Forms.FolderBrowserDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de parcourir, créer et éventuellement sélectionner un dossier|  
||Contrôle <xref:System.Windows.Forms.SaveFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs d'enregistrer un fichier.|  
|Contrôles de menu|Contrôle <xref:System.Windows.Forms.MenuStrip>|Crée des menus personnalisés. **Note:**  Le <xref:System.Windows.Forms.MenuStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.MainMenu>.|  
||Contrôle <xref:System.Windows.Forms.ContextMenuStrip>|Crée des menus contextuels personnalisés. **Note:**  Le contrôle <xref:System.Windows.Forms.ContextMenuStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.ContextMenu>.|  
|Commandes|Contrôle <xref:System.Windows.Forms.Button>|Démarre, arrête ou interrompt un processus.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d'un lien de style Web et déclenche un événement lorsque l'utilisateur clique sur le texte spécial.  En général, le texte est un lien vers une autre fenêtre ou vers un site Web.|  
||Contrôle <xref:System.Windows.Forms.NotifyIcon>|Affiche dans la zone d'état de la barre des tâches une icône qui représente une application s'exécutant en arrière\-plan.|  
||Contrôle <xref:System.Windows.Forms.ToolStrip>|Crée des barres d'outils qui peuvent avoir une apparence ou un comportement de type Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer ou personnalisé, avec ou sans thèmes, et avec prise en charge du dépassement de capacité et le reclassement des éléments au moment de l'exécution. **Note:**  Le contrôle <xref:System.Windows.Forms.ToolStrip> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.ToolBar>.|  
|Aide utilisateur|Composant <xref:System.Windows.Forms.HelpProvider>|Fournit une aide contextuelle ou en ligne pour les contrôles.|  
||Composant <xref:System.Windows.Forms.ToolTip>|Fournit une fenêtre indépendante qui affiche une brève description de la fonction d'un contrôle lorsque l'utilisateur place le pointeur au\-dessus du contrôle.|  
|Groupement d'autres contrôles|Contrôle <xref:System.Windows.Forms.Panel>|Groupe plusieurs contrôles à l'intérieur d'un frame déroulant dépourvu d'étiquette.|  
||Contrôle <xref:System.Windows.Forms.GroupBox>|Groupe plusieurs contrôles \(tels que des cases d'option\) dans un frame non déroulant doté d'une étiquette.|  
||Contrôle <xref:System.Windows.Forms.TabControl>|Fournit une page d'onglets permettant d'organiser efficacement les objets groupés et d'y d'accéder.|  
||Contrôle <xref:System.Windows.Forms.SplitContainer>|Fournit deux panneaux séparés par une barre mobile. **Note:**  Le contrôle <xref:System.Windows.Forms.SplitContainer> est conçu pour remplacer le contrôle <xref:System.Windows.Forms.Splitter>.|  
||Contrôle <xref:System.Windows.Forms.TableLayoutPanel>|Représente un panneau qui dispose dynamiquement son contenu dans une grille composée de lignes et de colonnes.|  
||Contrôle <xref:System.Windows.Forms.FlowLayoutPanel>|Représente un panneau qui présente dynamiquement son contenu, horizontalement ou verticalement.|  
|Audio|Contrôle <xref:System.Media.SoundPlayer>|Lit des fichiers audio au format .wav.  Les sons peuvent être chargés ou peuvent lus de façon asynchrone.|  
  
## Contrôles et composants remplacés par fonction  
  
|Fonction|Contrôle remplacé|Remplacement recommandé|  
|--------------|-----------------------|-----------------------------|  
|Affichage de données|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Affichage d'informations \(contrôles en lecture seule\)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Contrôles de menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Commandes|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Présentation des formulaires|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## Voir aussi  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)