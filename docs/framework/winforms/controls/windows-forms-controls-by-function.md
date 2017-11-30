---
title: "Classement par fonction des contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c49c42b02511fea66c88544bf689b2b05e788ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-controls-by-function"></a>Classement par fonction des contrôles Windows Forms
Windows Forms offre des contrôles et composants qui effectuent des fonctions. Le tableau suivant répertorie les contrôles Windows Forms et les composants en fonction de la fonction générale. En outre, il existe plusieurs contrôles qui remplissent la même fonction, le contrôle recommandé est répertorié avec une remarque concernant le contrôle, il est remplacé. Dans une table suivante distincte, les contrôles remplacés sont répertoriés avec leurs remplacements recommandés.  
  
> [!NOTE]
>  Les tables suivantes ne répertorient pas chaque contrôle ou composant, que vous pouvez utiliser dans les Windows Forms ; pour une liste plus complète, consultez [contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Contrôles et composants par fonction recommandés  
  
|Fonction|Contrôle|Description|  
|--------------|-------------|-----------------|  
|Affichage des données|Contrôle <xref:System.Windows.Forms.DataGridView>|Le <xref:System.Windows.Forms.DataGridView> contrôle fournit une table personnalisable pour l’affichage des données. La <xref:System.Windows.Forms.DataGridView> classe permet la personnalisation des cellules, lignes, colonnes et les bordures. **Remarque :** le <xref:System.Windows.Forms.DataGridView> contrôle fournit de nombreuses fonctionnalités de base et avancées qui sont manquantes dans le <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations, consultez [différences entre les Windows Forms contrôles DataGridView et DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Liaison de données et de navigation|<xref:System.Windows.Forms.BindingSource>composant|Simplifie la liaison des contrôles d’un formulaire de données en fournissant la gestion des devises, de notification de modification et d’autres services.|  
||Contrôle <xref:System.Windows.Forms.BindingNavigator>|Fournit une interface de type de la barre d’outils pour parcourir et de manipuler des données sur un formulaire.|  
|Édition de texte|Contrôle <xref:System.Windows.Forms.TextBox>|Affiche le texte entré au moment du design qui peut être modifié par l’utilisateur en cours d’exécution, ou par programme.|  
||Contrôle <xref:System.Windows.Forms.RichTextBox>|Active le texte à afficher avec mise en forme en texte brut ou le format RTF (RICH).|  
||Contrôle <xref:System.Windows.Forms.MaskedTextBox>|Contraint le format d’entrée d’utilisateur|  
|Affichage d’informations (en lecture seule)|Contrôle <xref:System.Windows.Forms.Label>|Affiche du texte que les utilisateurs ne peuvent pas directement modifier.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d’un lien de style Web et déclenche un événement lorsque l’utilisateur clique sur le texte spécial. Généralement, le texte est un lien vers une autre fenêtre ou un site Web.|  
||Contrôle <xref:System.Windows.Forms.StatusStrip>|Affiche des informations sur l’état actuel de l’application à l’aide de la zone délimitée, généralement au bas d’un formulaire parent.|  
||Contrôle <xref:System.Windows.Forms.ProgressBar>|Affiche l’état d’avancement d’une opération à l’utilisateur.|  
|Affichage de page Web|Contrôle <xref:System.Windows.Forms.WebBrowser>|Autorise l'utilisateur à parcourir des pages web dans votre formulaire.|  
|Sélection dans une liste|Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d’éléments, accompagnés chacun d’une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.ComboBox>|Affiche une liste déroulante d’éléments.|  
||Contrôle <xref:System.Windows.Forms.DomainUpDown>|Affiche une liste d’éléments de texte que les utilisateurs peuvent parcourir avec des boutons haut et bas.|  
||Contrôle <xref:System.Windows.Forms.ListBox>|Affiche la liste des éléments texte et graphiques (icônes).|  
||Contrôle <xref:System.Windows.Forms.ListView>|Affiche les éléments dans un des quatre modes différents. Les vues inclure uniquement du texte, du texte avec petites icônes, texte avec grandes icônes et un mode Détails.|  
||Contrôle <xref:System.Windows.Forms.NumericUpDown>|Affiche une liste de nombres que les utilisateurs peuvent parcourir avec des boutons haut et bas.|  
||Contrôle <xref:System.Windows.Forms.TreeView>|Affiche une collection hiérarchique d’objets nœud qui peut être constitué de texte avec des cases à cocher facultatives ou des icônes.|  
|Affichage de graphiques|Contrôle <xref:System.Windows.Forms.PictureBox>|Affiche les fichiers graphiques, tels que les images bitmaps et icônes, dans un frame.|  
|Stockage des graphismes|Contrôle <xref:System.Windows.Forms.ImageList>|Sert de référentiel pour les images. <xref:System.Windows.Forms.ImageList>contrôles et les images qu’ils contiennent peuvent être réutilisés à partir d’une application à l’autre.|  
|Paramètre de valeur|Contrôle <xref:System.Windows.Forms.CheckBox>|Affiche une case à cocher et une étiquette de texte. Généralement utilisé pour définir les options.|  
||Contrôle <xref:System.Windows.Forms.CheckedListBox>|Affiche une liste déroulante d’éléments, accompagnés chacun d’une case à cocher.|  
||Contrôle <xref:System.Windows.Forms.RadioButton>|Affiche un bouton qui peut être activé ou désactivée.|  
||Contrôle <xref:System.Windows.Forms.TrackBar>|Permet aux utilisateurs de définir des valeurs sur une échelle en déplaçant un « pouce » le long d’une échelle.|  
|Paramètre de date|Contrôle <xref:System.Windows.Forms.DateTimePicker>|Affiche un calendrier graphique permettant aux utilisateurs de sélectionner une date ou une heure.|  
||Contrôle <xref:System.Windows.Forms.MonthCalendar>|Affiche un calendrier graphique permettant aux utilisateurs de sélectionner une plage de dates.|  
|Boîtes de dialogue|Contrôle <xref:System.Windows.Forms.ColorDialog>|Affiche la boîte de dialogue de sélecteur de couleur qui permet aux utilisateurs de définir la couleur d’un élément d’interface.|  
||Contrôle <xref:System.Windows.Forms.FontDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de définir une police et ses attributs.|  
||Contrôle <xref:System.Windows.Forms.OpenFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs d’accéder à et sélectionnez un fichier.|  
||Contrôle <xref:System.Windows.Forms.PrintDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de sélectionner une imprimante et définissez ses attributs.|  
||Contrôle <xref:System.Windows.Forms.PrintPreviewDialog>|Affiche une boîte de dialogue qui affiche un contrôle <xref:System.Drawing.Printing.PrintDocument> composant apparaîtra une fois imprimé.|  
||Contrôle <xref:System.Windows.Forms.FolderBrowserDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs de parcourir, créer et éventuellement sélectionner un dossier|  
||Contrôle <xref:System.Windows.Forms.SaveFileDialog>|Affiche une boîte de dialogue qui permet aux utilisateurs d’enregistrer un fichier.|  
|Contrôles de menu|Contrôle <xref:System.Windows.Forms.MenuStrip>|Crée des menus personnalisés. **Remarque :** le <xref:System.Windows.Forms.MenuStrip> est conçu pour remplacer le <xref:System.Windows.Forms.MainMenu> contrôle.|  
||Contrôle <xref:System.Windows.Forms.ContextMenuStrip>|Crée des menus contextuels personnalisés. **Remarque :** le <xref:System.Windows.Forms.ContextMenuStrip> est conçu pour remplacer le <xref:System.Windows.Forms.ContextMenu> contrôle.|  
|Commandes|Contrôle <xref:System.Windows.Forms.Button>|Démarre, arrête ou interrompt un processus.|  
||Contrôle <xref:System.Windows.Forms.LinkLabel>|Affiche le texte sous la forme d’un lien de style Web et déclenche un événement lorsque l’utilisateur clique sur le texte spécial. Généralement, le texte est un lien vers une autre fenêtre ou un site Web.|  
||Contrôle <xref:System.Windows.Forms.NotifyIcon>|Affiche une icône dans la zone de notification d’état de la barre des tâches qui représente une application en cours d’exécution en arrière-plan.|  
||Contrôle <xref:System.Windows.Forms.ToolStrip>|Crée des barres d’outils qui peuvent avoir un Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer ou personnalisé apparence, avec ou sans thèmes et avec prise en charge de dépassement de capacité et la réorganisation des éléments au moment de l’exécution. **Remarque :** le <xref:System.Windows.Forms.ToolStrip> contrôle est conçu pour remplacer le <xref:System.Windows.Forms.ToolBar> contrôle.|  
|Aide de l’utilisateur|<xref:System.Windows.Forms.HelpProvider>composant|Fournit une aide contextuelle ou en ligne pour les contrôles.|  
||<xref:System.Windows.Forms.ToolTip>composant|Fournit une fenêtre contextuelle qui affiche une brève description de l’objectif d’un contrôle lorsque l’utilisateur place le pointeur sur le contrôle.|  
|Regrouper les autres contrôles.|Contrôle <xref:System.Windows.Forms.Panel>|Regroupe un ensemble de contrôles sur un frame déroulant sans étiquette.|  
||Contrôle <xref:System.Windows.Forms.GroupBox>|Regroupe un ensemble de contrôles (tels que des boutons radio) sur un frame non déroulant doté étiqueté.|  
||Contrôle <xref:System.Windows.Forms.TabControl>|Fournit une page à onglets pour organiser et d’y accéder efficacement les objets groupés.|  
||Contrôle <xref:System.Windows.Forms.SplitContainer>|Fournit deux panneaux séparés par une barre mobile. **Remarque :** le <xref:System.Windows.Forms.SplitContainer> contrôle est conçu pour remplacer le <xref:System.Windows.Forms.Splitter> contrôle.|  
||Contrôle <xref:System.Windows.Forms.TableLayoutPanel>|Représente un panneau qui dispose dynamiquement son contenu dans une grille composée de lignes et de colonnes.|  
||Contrôle <xref:System.Windows.Forms.FlowLayoutPanel>|Représente un panneau qui dispose dynamiquement son contenu horizontalement ou verticalement.|  
|Audio|Contrôle <xref:System.Media.SoundPlayer>|La lecture des fichiers audio au format .wav. Sons peuvent être chargés ou lu de manière asynchrone.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Contrôles et composants par fonction remplacés  
  
|Fonction|Contrôle remplacé|Remplacement recommandé|  
|--------------|------------------------|-----------------------------|  
|Affichage des données|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Affichage d’informations (contrôles en lecture seule)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Contrôles de menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Commandes|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Présentation des formulaires|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
