---
title: "Comment&#160;: parcourir un DataSet avec le contr&#244;le BindingNavigator Windows Forms | Microsoft Docs"
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
  - "BindingNavigator (contrôle Windows Forms), naviguer entre des groupes de données"
  - "groupes de données (Windows Forms), naviguer entre"
  - "exemples (Windows Forms), BindingNavigator (contrôle)"
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: parcourir un DataSet avec le contr&#244;le BindingNavigator Windows Forms
Quand vous générez des applications pilotées par les données, vous devez souvent présenter des collections de données aux utilisateurs.  Le contrôle <xref:System.Windows.Forms.BindingNavigator>, associé au composant <xref:System.Windows.Forms.BindingSource>, fournit une solution pratique et extensible pour parcourir une collection et afficher des éléments de façon séquentielle.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser un contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir des données.  Le jeu est contenu dans un <xref:System.Data.DataView>, qui est lié à un contrôle <xref:System.Windows.Forms.TextBox> avec un composant <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Le stockage d'informations sensibles \(telles qu'un mot de passe\) dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)