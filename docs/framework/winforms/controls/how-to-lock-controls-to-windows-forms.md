---
title: "Comment&#160;: verrouiller des contr&#244;les sur des Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), verrouiller"
  - "contrôles Windows Forms, verrouiller"
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: verrouiller des contr&#244;les sur des Windows Forms
Lorsque vous créez l'interface utilisateur de votre application Windows, vous pouvez verrouiller les contrôles une fois qu'ils sont correctement placés, afin de ne pas risquer de les déplacer ou de les redimensionner par inadvertance en définissant d'autres propriétés.  
  
 En outre, vous pouvez verrouiller et déverrouiller en même temps tous les contrôles d'un formulaire, ce qui est utile lorsque le formulaire en compte beaucoup ; vous pouvez également déverrouiller des contrôles individuels.  Après avoir disposé tous les contrôles à l'endroit souhaité du formulaire, verrouillez\-les pour prévenir tout déplacement accidentel.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour verrouiller un contrôle  
  
1.  Dans la fenêtre **Propriétés**, cliquez sur la propriété **Locked** et sélectionnez `true`.  \(double\-cliquez sur le nom de la propriété pour faire alterner sa valeur\).  
  
     Vous pouvez également cliquer avec le bouton droit sur le contrôle, puis sélectionner **Verrouiller les contrôles**.  
  
    > [!NOTE]
    >  Le verrouillage des contrôles empêche leur redimensionnement ou leur déplacement sur l'aire de conception.  Il reste néanmoins possible de modifier leur taille ou leur position par le biais de la fenêtre **Propriétés** ou du code.  
  
### Pour verrouiller tous les contrôles d'un formulaire  
  
1.  Dans le menu **Format**, sélectionnez **Verrouiller les contrôles**.  
  
    > [!NOTE]
    >  Cette commande verrouille également la taille du formulaire, car un formulaire est un contrôle.  
  
### Pour déverrouiller tous les contrôles verrouillés d'un formulaire  
  
1.  Dans le menu **Format**, sélectionnez **Verrouiller les contrôles**.  
  
     Tous les contrôles précédemment verrouillés du formulaire sont maintenant déverrouillés.  
  
### Pour déverrouiller un contrôle individuel  
  
1.  Dans la fenêtre **Propriétés**, cliquez sur la propriété **Locked** et sélectionnez `false`.  \(double\-cliquez sur le nom de la propriété pour faire alterner sa valeur\).  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)