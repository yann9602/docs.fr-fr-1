---
title: "Proc&#233;dure pas &#224; pas&#160;: mappage de propri&#233;t&#233; &#224; l&#39;aide du contr&#244;le ElementHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ElementHost (contrôle), mapper des propriétés"
  - "mapper des propriétés"
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Proc&#233;dure pas &#224; pas&#160;: mappage de propri&#233;t&#233; &#224; l&#39;aide du contr&#244;le ElementHost
Cette procédure pas à pas montre comment utiliser la propriété <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> pour mapper des propriétés [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à des propriétés correspondantes sur un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   création du projet ;  
  
-   Définition d'un nouveau mappage de propriété.  
  
-   Suppression d'un mappage de propriété par défaut.  
  
-   Extension d'un mappage de propriété par défaut.  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [Mappage de propriété à l'aide du contrôle ElementHost, exemple](http://go.microsoft.com/fwlink/?LinkID=160018).  
  
 À la fin de cette procédure, vous saurez mapper des propriétés [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à des propriétés correspondantes sur un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## Création du projet  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nommé `PropertyMappingWithElementHost`.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans l'Explorateur de solutions, ajoutez une référence aux assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  Copiez le code suivant en haut du fichier de code `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Ouvrez `Form1` dans le Concepteur Windows Forms.  Double\-cliquez sur le formulaire pour ajouter un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Form.Load>.  
  
5.  Revenez au Concepteur Windows Forms et ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Resize> du formulaire.  Pour plus d'informations, consultez [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/fr-fr/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
6.  Déclarez un champ <xref:System.Windows.Forms.Integration.ElementHost> dans la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## Définition de nouveaux mappages de propriétés  
 Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> fournit plusieurs mappages de propriétés par défaut.  Vous ajoutez un nouveau mappage de propriété en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
#### Pour définir de nouveaux mappages de propriétés  
  
1.  Copiez le code suivant dans la définition de la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     La méthode `AddMarginMapping` ajoute un nouveau mappage à la propriété <xref:System.Windows.Forms.Control.Margin%2A>.  
  
     La méthode `OnMarginChange` traduit la propriété <xref:System.Windows.Forms.Control.Margin%2A> en propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
2.  Copiez le code suivant dans la définition de la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     La méthode `AddRegionMapping` ajoute un nouveau mappage à la propriété <xref:System.Windows.Forms.Control.Region%2A>.  
  
     La méthode `OnRegionChange` traduit la propriété <xref:System.Windows.Forms.Control.Region%2A> en propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.  
  
     La méthode `Form1_Resize` gère l'événement <xref:System.Windows.Forms.Control.Resize> du formulaire et ajuste la taille de la zone de découpage à l'élément hébergé.  
  
## Suppression d'un mappage de propriété par défaut  
 Supprimez un mappage de propriété par défaut en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
#### Pour supprimer un mappage de propriété par défaut  
  
-   Copiez le code suivant dans la définition de la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     La méthode `RemoveCursorMapping` supprime le mappage par défaut pour la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.  
  
## Extension d'un mappage de propriété par défaut  
 Vous pouvez utiliser un mappage de propriété par défaut et l'étendre avec votre propre mappage.  
  
#### Pour étendre un mappage de propriété par défaut  
  
-   Copiez le code suivant dans la définition de la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     La méthode `ExtendBackColorMapping` ajoute un traducteur de propriété personnalisé au mappage de propriété <xref:System.Windows.Forms.Control.BackColor%2A> existant.  
  
     La méthode `OnBackColorChange` affecte une image spécifique à la propriété <xref:System.Windows.Controls.Control.Background%2A> du contrôle hébergé.  La méthode `OnBackColorChange` est appelée après application du mappage de propriété par défaut.  
  
## Initialisation de vos mappages de propriété  
  
#### Pour initialiser vos mappages de propriété  
  
1.  Copiez le code suivant dans la définition de la classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     La méthode `Form1_Load` traite l'événement <xref:System.Windows.Forms.Form.Load> et exécute l'initialisation suivante.  
  
    -   Crée un élément <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    -   Appelle la méthode que vous avez définie précédemment au cours de cette procédure pour paramétrer les mappages de propriété.  
  
    -   Affecte des valeurs initiales aux propriétés mappées.  
  
2.  Appuyez sur F5 pour générer et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)