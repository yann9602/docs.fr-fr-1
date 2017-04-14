---
title: "Comment&#160;: cr&#233;er un contr&#244;le &#224; liaison simple dans un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "liaison de données, liaison de données simple"
  - "contrôles Windows Forms, liaison de données"
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un contr&#244;le &#224; liaison simple dans un Windows Form
La *liaison simple* permet d'afficher un seul élément de données, tel qu'une valeur de colonne d'une table du groupe de données, dans un contrôle.  Vous pouvez créer une liaison simple entre n'importe quelle propriété d'un contrôle et une valeur de données.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer une liaison simple d'un contrôle  
  
1.  se connecter à une source de données ;  Pour plus d'informations, consultez [Connexion à une source de données](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Dans le formulaire, sélectionnez le contrôle et affichez la fenêtre **Propriétés**.  
  
3.  Développez la propriété **\(DataBindings\)**.  
  
     Les propriétés les plus souvent liées sont affichées sous la propriété **\(DataBindings\)**.  Par exemple, dans la plupart des contrôles, la propriété **Text** est la plus souvent liée.  
  
4.  Si la propriété que vous souhaitez lier ne fait pas partie des propriétés les plus souvent liées, cliquez sur le bouton de **sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) dans la zone **\(Avancées\)** pour afficher la boîte de dialogue **Mise en forme et liaison avancée** avec une liste complète des propriétés pour ce contrôle.  
  
5.  Sélectionnez la propriété que vous souhaitez lier et cliquez sur la flèche de déroulement sous **Liaison**.  
  
     Une liste des sources de données disponibles s'affiche.  
  
6.  Développez la source de données que vous souhaitez lier jusqu'à ce que vous localisiez l'élément de données qui vous intéresse.  Par exemple, si vous créez une liaison à la valeur d'une colonne d'une table du groupe de données, développez le nom du groupe de données, puis le nom de la table afin d'afficher les noms des colonnes.  
  
7.  Cliquez sur le nom d'un élément auquel les données vont être liées.  
  
8.  Si vous utilisiez la boîte de dialogue **Mise en forme et liaison avancée**, cliquez sur **OK** pour revenir à la fenêtre **Propriétés**.  
  
9. Pour lier d'autres propriétés du contrôle, répétez les étapes 3 à 7.  
  
    > [!NOTE]
    >  Dans la mesure où les contrôles à liaison simple n'affichent qu'un seul élément de données, il est fréquent d'ajouter une logique de navigation à un Windows Form contenant des contrôles à liaison simple.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Binding>   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)