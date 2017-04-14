---
title: "Comment&#160;: emp&#234;cher l&#39;ajout et la suppression de lignes dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), empêcher l'ajout ou la suppression de ligne"
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: emp&#234;cher l&#39;ajout et la suppression de lignes dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Quelquefois vous souhaiterez empêcher les utilisateurs d'entrer de nouvelles lignes de données ou de supprimer des lignes existantes dans votre contrôle <xref:System.Windows.Forms.DataGridView>.  Les nouvelles lignes sont entrées dans la ligne spéciale pour les nouveaux enregistrements en bas de contrôle.  Lorsque vous désactivez l'ajout de ligne, la ligne pour les nouveaux enregistrements n'est pas affichée.  Vous pouvez rendre ensuite le contrôle entièrement en lecture seule en désactivant la suppression des lignes et la modification des cellules.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour empêcher l'ajout et la suppression de lignes  
  
-   Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis désactivez les cases à cocher **Activer l'ajout** et **Activer la suppression**.  
  
    > [!NOTE]
    >  Pour rendre le contrôle entièrement en lecture seule, désactivez aussi la case à cocher **Autoriser les modifications**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=fullName>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)