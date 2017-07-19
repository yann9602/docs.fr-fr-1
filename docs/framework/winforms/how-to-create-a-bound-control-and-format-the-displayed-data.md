---
title: "Comment&#160;: cr&#233;er un contr&#244;le d&#233;pendant et mettre en forme les donn&#233;es affich&#233;es | Microsoft Docs"
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
  - "contrôles dépendants (Windows Forms), créer"
  - "contrôles dépendants (Windows Forms), mettre en forme des données"
  - "données (Windows Forms), mettre en forme"
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er un contr&#244;le d&#233;pendant et mettre en forme les donn&#233;es affich&#233;es
Avec la liaison de données Windows Forms, vous pouvez mettre en forme les données affichées dans un contrôle lié aux données à l'aide de la boîte de dialogue **Mise en forme et liaison avancée**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour lier un contrôle et mettre en forme les données affichées  
  
1.  Connectez\-vous à une source de données.  
  
     Pour plus d'informations, consultez [Connexion à une source de données](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Dans le formulaire, sélectionnez le contrôle, puis ouvrez la fenêtre Propriétés.  
  
3.  Développez la propriété **\(DataBindings\)** puis, dans la zone **\(Avancé\)**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour afficher la boîte de dialogue **Mise en forme et liaison avancée**, qui présente une liste complète des propriétés de ce contrôle.  
  
4.  Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche **Liaison**.  
  
     Une liste des sources de données disponibles s'affiche.  
  
5.  Développez la source de données avec laquelle vous voulez établir une liaison jusqu'à trouver l'élément de données souhaité.  
  
     Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.  
  
6.  Cliquez sur le nom d'un élément avec lequel établir une liaison.  
  
7.  Dans la zone **Type de format**, cliquez sur le format à appliquer aux données affichées dans le contrôle.  
  
     Dans tous les cas, vous pouvez spécifier la valeur affichée dans le contrôle si la source de données contient <xref:System.DBNull>.  Sinon, les options varient légèrement en fonction du type de format que vous choisissez.  Le tableau suivant présente les options et les types de format.  
  
    |Type de format|Option de mise en forme|  
    |--------------------|-----------------------------|  
    |Aucune mise en forme|Aucune option.|  
    |Numérique|Spécifiez le nombre de décimales à l'aide du contrôle **Nombre de décimales**.|  
    |Devise|Spécifiez le nombre de décimales à l'aide du contrôle **Nombre de décimales**.|  
    |Date et heure|Sélectionnez comment la date et l'heure doivent être affichées en sélectionnant l'un des éléments dans la zone de sélection **Type**.|  
    |Scientifique|Spécifiez le nombre de décimales à l'aide du contrôle **Nombre de décimales**.|  
    |Personnalisé|Spécifiez une chaîne de format personnalisée.<br /><br /> Pour plus d'informations, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md). **Note:**  Il n'est pas garanti que les chaînes de format personnalisées puissent effectuer un aller\-retour entre la source de données et le contrôle dépendant.  Gérez plutôt l'événement <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> pour la liaison et appliquez la mise en forme personnalisée dans le code de gestion d'événements.|  
  
8.  Cliquez sur **OK** pour fermer la boîte de dialogue **Mise en forme et liaison avancée** et revenir à la fenêtre Propriétés.  
  
## Voir aussi  
 [Comment : créer un contrôle à liaison simple dans un Windows Form](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)   
 [Validation des entrées d'utilisateur dans les Windows Forms](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)