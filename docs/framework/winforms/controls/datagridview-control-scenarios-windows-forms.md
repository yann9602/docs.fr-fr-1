---
title: "Scénarios du contrôle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 919197d8fdb40f0e0fb7b91fecae38f4e0e061bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scénarios du contrôle DataGridView (Windows Forms)
Avec la <xref:System.Windows.Forms.DataGridView> (contrôle), vous pouvez afficher des données tabulaires provenant de diverses sources de données. Pour les utilisations simples, vous pouvez remplir manuellement un <xref:System.Windows.Forms.DataGridView> et manipuler les données directement via le contrôle. En général, toutefois, stockez vos données dans une source de données externe et la lier le contrôle à par le biais d’un <xref:System.Windows.Forms.BindingSource> composant.  
  
 Cette rubrique décrit certains scénarios courants qui impliquent le <xref:System.Windows.Forms.DataGridView> contrôle.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scénario 1 : Affichage de petites quantités de données  
 Vous n’êtes pas obligé de stocker vos données dans une source de données externe pour l’afficher dans la <xref:System.Windows.Forms.DataGridView> contrôle. Si vous travaillez avec une petite quantité de données, vous pouvez remplir le contrôle vous-même et manipuler les données via le contrôle. Il s’agit *mode indépendant*. Pour plus d’informations, consultez [Comment : créer un contrôle de DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   En mode indépendant, vous remplissez le contrôle manuellement.  
  
-   Le mode indépendant est particulièrement adapté aux petites quantités de données en lecture seule.  
  
-   Le mode indépendant est également adapté pour les tables de feuille de calcul ou peuplées.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scénario 2 : Afficher et mettre à jour les données stockées dans une Source de données externes  
 Vous pouvez utiliser la <xref:System.Windows.Forms.DataGridView> contrôle comme une interface utilisateur (IU) par lesquels les utilisateurs peuvent accéder aux données conservées dans une source de données comme une table de base de données ou une collection d’objets métier. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   Mode dépendant vous permet de vous connecter à une source de données, de générer automatiquement des colonnes basées sur les propriétés de source de données ou les colonnes de base de données et de remplir automatiquement le contrôle.  
  
-   Mode dépendant est adapté pour l’interaction utilisateur élevée avec des données. Données peuvent être mise en forme pour l’affichage et spécifié par l’utilisateur des données peuvent être analysées dans le format attendu par la source de données. Entrée de données mise en forme d’erreurs et les erreurs de contrainte de base de données peut être détectée afin que les utilisateurs peuvent être avertis et les cellules erronées corrigées.  
  
-   Des fonctionnalités supplémentaires telles que le tri de la colonne, gel et réorganisation permettent aux utilisateurs d’afficher les données de la façon la plus pratique pour leur flux de travail.  
  
-   Prise en charge du Presse-papiers permet aux utilisateurs de copier des données à partir de votre application dans d’autres applications.  
  
## <a name="scenario-3-advanced-data"></a>Scénario 3 : Avancée des données  
 Si vous avez des besoins particuliers du modèle de liaison de données standard ne traite pas, vous pouvez gérer l’interaction entre le contrôle et vos données en implémentant *mode virtuel*. Implémentation du mode virtuel correspond à un ou plusieurs gestionnaires d’événements qui permettent les contrôle demander des informations sur les cellules que les informations de mise en œuvre est nécessaire.  
  
 Par exemple, si vous travaillez avec de grandes quantités de données, vous souhaiterez implémenter le mode virtuel pour assurer une efficacité optimale. Mode virtuel est également utile pour maintenir les valeurs de colonnes indépendantes que vous affichez en même temps que les colonnes extraites d’une autre source de données.  
  
 Pour plus d’informations sur le mode virtuel, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   Mode virtuel est adapté pour l’affichage de très grandes quantités de données lorsque vous avez besoin optimiser les performances.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scénario 4 : Redimensionner automatiquement des lignes et des colonnes  
 Lorsque vous affichez des données qui sont régulièrement mis à jour, vous pouvez redimensionner automatiquement des lignes et des colonnes pour s’assurer que tout le contenu est visible. Le <xref:System.Windows.Forms.DataGridView> contrôle fournit plusieurs options qui vous permettent d’activer ou désactiver redimensionnement manuel, redimensionner par programmation à des moments spécifiques ou de redimensionner automatiquement chaque fois que du contenu change. Pour plus d’informations, consultez [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   Redimensionnement manuel permet aux utilisateurs d’ajuster la largeur et la hauteur de cellule.  
  
-   Le redimensionnement automatique vous permet de maintenir des tailles de cellule afin que le contenu de la cellule n’est jamais tronqué.  
  
-   Le redimensionnement par programmation vous permet de redimensionner des cellules à des moments spécifiques afin d’éviter l’altération des performances de redimensionnement automatique continue.  
  
## <a name="scenario-5-simple-customization"></a>Scénario 5 : Personnalisation Simple  
 Le <xref:System.Windows.Forms.DataGridView> contrôle offre vous permet de modifier l’apparence de base et son comportement de nombreuses manières. Pour plus d’informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle>objets vous permettent de fournir la couleur, la police, la mise en forme et des informations de positionnement à plusieurs niveaux et pour les éléments individuels du contrôle.  
  
-   Styles de cellules peuvent être en couches et partagés par plusieurs éléments, ce qui vous permet de réutiliser le code.  
  
## <a name="scenario-6-advanced-customization"></a>Scénario 6 : Personnalisation avancée  
 Le <xref:System.Windows.Forms.DataGridView> contrôle offre vous permettent de personnaliser son apparence et son comportement de nombreuses manières.  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
-   Vous pouvez fournir votre propre code de peinture de cellule. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Vous pouvez fournir votre propre peinture de ligne. Cela est utile, par exemple, pour créer des lignes avec du contenu qui s’étend sur plusieurs colonnes. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Vous pouvez implémenter vos propres classes de cellule et de colonne pour personnaliser l’apparence de la cellule. Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms à l’apparence et le comportement de leur extension](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Vous pouvez implémenter vos propres classes de cellule et de colonne pour héberger des contrôles autres que ceux fournis par les types de colonne intégrés. Pour plus d’informations, consultez [Comment : héberger des contrôles dans les cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 [Vue d’ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
