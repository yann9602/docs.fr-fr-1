---
title: "Comment&#160;: figer les colonnes du contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), bloquer"
  - "données (Windows Forms), afficher"
  - "DataGridView (contrôle Windows Forms), blocage des colonnes"
  - "Windows Forms, colonnes"
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: figer les colonnes du contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Lorsque les utilisateurs consultent des données affichées dans un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms, ils doivent quelquefois se reporter fréquemment à une colonne seule ou à un jeu de colonnes.  Par exemple, lorsque vous affichez une table des informations client qui contient beaucoup de colonnes, il est utile d'afficher le nom du client en permanence tout en laissant d'autres colonnes défiler à l'extérieur de la région visible.  
  
 Pour obtenir ce comportement, vous pouvez figer les colonnes dans le contrôle.  Lorsque vous figez une colonne, toutes les colonnes à sa gauche \(ou à sa droite dans les scripts de langues s'écrivant de droite à gauche\) sont figées aussi.  Les colonnes figées restent en place pendant que toutes les autres colonnes peuvent défiler.  Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées.  Les utilisateurs peuvent repositionner les colonnes dans l'un et l'autre de groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour figer une colonne à l'aide du concepteur  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Dans la grille **Propriétés des colonnes**, affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> la valeur `true`.  
  
    > [!NOTE]
    >  Vous pouvez également figer une colonne lors de son ajout en sélectionnant la zone **Figé** de la boîte de dialogue **Ajouter une colonne**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)   
 [How to: Display Right\-to\-Left Text in Windows Forms for Globalization](http://msdn.microsoft.com/fr-fr/f0663385-2354-4c65-8676-706422283b14)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)