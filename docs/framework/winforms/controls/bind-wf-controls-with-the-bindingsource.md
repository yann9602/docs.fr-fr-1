---
title: "Comment&#160;: lier des contr&#244;les Windows Forms au composant BindingSource &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "BindingSource (composant Windows Forms), lier des contrôles"
  - "contrôles (Windows Forms), liaison"
  - "liaison de données, BindingSource (composant)"
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: lier des contr&#244;les Windows Forms au composant BindingSource &#224; l&#39;aide du concepteur
Une fois que vous avez ajouté des contrôles à votre formulaire et déterminé l'interface utilisateur de votre application, vous pouvez lier les contrôles à une source de données, afin que les utilisateurs puissent modifier et enregistrer des données relatives à l'application au moment de l'exécution.  
  
 La liaison d'un contrôle ou d'une série de contrôles dans Windows Forms est plus facile si vous utilisez le contrôle <xref:System.Windows.Forms.BindingSource> comme pont entre les contrôles du formulaire et de la source de données.  
  
 Un ou plusieurs contrôles d'un formulaire peuvent être liés aux données ; dans la procédure suivante, un contrôle <xref:System.Windows.Forms.TextBox> est lié à une source de données.  
  
 Pour terminer la procédure, vous devez établir une liaison à une source de données dérivée d'une base de données.  Pour plus d'informations sur la création de sources de données issues d'autres magasins de données, consultez [Vue d'ensemble des sources de données](../Topic/Add%20new%20data%20sources.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour lier un contrôle au moment du design  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> dans le formulaire.  
  
2.  Dans la fenêtre **Propriétés** :  
  
    1.  Développez le nœud **\(DataBindings\)**.  
  
    2.  Cliquez sur la flèche en regard de la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
         L'éditeur de types muni d'une interface utilisateur **DataSource** s'ouvre.  
  
         Si une source de données a été configurée précédemment pour le projet ou pour le formulaire, elle apparaît.  
  
3.  Cliquez sur **Ajouter une source de données au projet** pour vous connecter aux données et créer une source de données.  
  
4.  Dans la page d'accueil de l'**Assistant Configuration de source de données**, cliquez sur **Suivant**.  
  
5.  Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**.  
  
6.  Sélectionnez une connexion de données dans la liste des connexions disponibles à la page **Choisir votre connexion de données**.  Si la connexion de données de votre choix n'est pas disponible, sélectionnez **Nouvelle connexion** pour en créer une nouvelle.  
  
7.  Choisissez **Oui, enregistrer la connexion** pour stocker la chaîne de connexion dans le fichier de configuration de l'application.  
  
8.  Sélectionnez les objets de base de données à insérer dans votre application.  Dans ce cas, sélectionnez un champ dans une table à afficher dans <xref:System.Windows.Forms.TextBox>.  
  
9. Remplacez le nom du groupe de données par défaut, le cas échéant.  
  
10. Cliquez sur **Terminer**.  
  
11. Dans la fenêtre **Propriétés**, cliquez de nouveau sur la flèche en regard de la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  Dans l'éditeur de types muni d'une interface utilisateur **DataSource**, sélectionnez le nom du champ auquel vous souhaitez lier <xref:System.Windows.Forms.TextBox>.  
  
     L'éditeur de types muni d'une interface utilisateur **DataSource** se ferme et le groupe de données, <xref:System.Windows.Forms.BindingSource> et l'adaptateur de table propre à cette connexion de données sont ajoutés à votre formulaire.  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [Vue d'ensemble des sources de données](../Topic/Add%20new%20data%20sources.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)