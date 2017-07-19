---
title: "Comment&#160;: ajouter et supprimer des colonnes dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.DataGridViewAddColumnDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGridView (contrôle Windows Forms), ajouter des colonnes"
  - "DataGridView (contrôle Windows Forms), supprimer des colonnes"
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: ajouter et supprimer des colonnes dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> doit contenir des colonnes pour afficher des données.  Si vous projetez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous\-même.  Autrement, vous pouvez lier le contrôle à une source de données qui génère et remplit automatiquement les colonnes.  Si la source de données contient plus de colonnes que vous souhaitez afficher, vous pouvez supprimer les colonnes non désirées.  
  
 La procédure suivante nécessite un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter une colonne à l'aide du concepteur  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Ajouter une colonne**.  
  
2.  Dans la boîte de dialogue **Ajouter une colonne**, choisissez l'option **Colonne liée aux données** et sélectionnez une colonne de la source de données ou choisissez l'option **Colonne indépendante** et définissez la colonne à l'aide des champs fournis.  
  
3.  Cliquez sur le bouton **Ajouter** pour ajouter la colonne ; celle\-ci en apparaît alors dans le concepteur si les colonnes existantes ne remplissent pas déjà la zone d'affichage du contrôle.  
  
    > [!NOTE]
    >  Vous pouvez modifier des propriétés des colonnes dans la boîte de dialogue **Modifier les colonnes** à laquelle vous pouvez accéder via la balise active du contrôle.  
  
### Pour supprimer une colonne à l'aide du concepteur  
  
1.  Choisissez **Modifier les colonnes** dans la balise active du contrôle.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Cliquez sur le bouton **Supprimer** pour supprimer la colonne, qui n'apparaît plus dans le concepteur.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)