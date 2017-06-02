---
title: "Comment&#160;: ajouter des contr&#244;les ActiveX aux Windows Forms | Microsoft Docs"
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
  - "ActiveX (contrôles Windows Forms), ajouter"
  - "formulaires, ajouter des contrôles ActiveX"
  - "contrôles Windows Forms, contrôles ActiveX"
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: ajouter des contr&#244;les ActiveX aux Windows Forms
Le Concepteur Windows Forms est tout particulièrement adapté aux contrôles Windows Forms ; toutefois, vous pouvez également placer des contrôles ActiveX dans les Windows Forms.  
  
> [!CAUTION]
>  Les performances des Windows Forms sont limitées lorsque des contrôles ActiveX leur sont ajoutés.  
  
 Avant d'ajouter des contrôles ActiveX à votre formulaire, vous devez les ajouter à la boîte à outils.  Pour plus d'informations, consultez [Composants COM, boîte de dialogue Personnaliser la boîte à outils](http://msdn.microsoft.com/fr-fr/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter un contrôle ActiveX à un Windows Form  
  
-   Double\-cliquez sur le contrôle dans la boîte à outils.  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ajoute toutes les références au contrôle figurant dans votre projet.  Pour plus d'informations sur les points à retenir lors de l'utilisation de contrôles ActiveX sur des Windows Forms, consultez [Considérations sur l'hébergement d'un contrôle ActiveX dans un Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  ActiveX Control Importer pour Windows Forms \(Aximp.exe\) crée des arguments d'événement d'un type différent de celui qui est attendu lors de l'importation de bibliothèques de liens dynamiques ActiveX.  Alors que l'argument `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` est attendu, les arguments créés par AxImp.exe sont semblables à ceci : `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`.  Sachez toutefois que cette anomalie n'empêche pas le code de fonctionner normalement.  Pour plus d'informations, consultez [Windows Forms ActiveX Control Importer \(Aximp.exe\)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/fr-fr/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)