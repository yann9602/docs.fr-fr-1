---
title: "Vue d&#39;ensemble du composant HelpProvider (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HelpProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "boîtes de dialogue, aide contextuelle"
  - "Aide F1, ajouter aux Windows Forms"
  - "Aide, ajouter aux applications Windows"
  - "HelpProvider (composant Windows Forms), à propos du composant HelpProvider"
  - "Windows Forms, aide contextuelle"
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Vue d&#39;ensemble du composant HelpProvider (Windows Forms)
Le composant [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) Windows Forms permet d'associer un fichier d'aide HTML Help 1.x \(fichier .chm généré par HTML Help Workshop ou fichier .htm\) à votre application Windows.  Vous pouvez fournir de l'aide via différentes méthodes :  
  
-   par l'affichage d'une aide contextuelle pour les contrôles des Windows Forms ;  
  
-   par l'affichage d'une aide contextuelle sur une boîte de dialogue spécifique ou sur certains contrôles d'une boîte de dialogue ;  
  
-   par l'ouverture d'un fichier d'aide dans des zones spécifiques \(page principale d'un sommaire, index ou fonction de recherche, par exemple\).  
  
## Utilisation du composant HelpProvider  
 L'ajout d'un composant <xref:System.Windows.Forms.HelpProvider> à votre Windows Form permet aux autres contrôles du formulaire d'exposer les propriétés d'aide du composant <xref:System.Windows.Forms.HelpProvider>.  Cela permet de fournir de l'aide pour les contrôles de votre Windows Form.  Vous pouvez associer un fichier d'aide au composant <xref:System.Windows.Forms.HelpProvider> au moyen de la propriété <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>.  Vous spécifiez le type d'aide fourni en appelant la méthode <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> et en fournissant une valeur de l'énumération <xref:System.Windows.Forms.HelpNavigator> pour le contrôle spécifié.  Vous fournissez le mot clé ou le sujet de l'aide en appelant la méthode <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.  
  
 Vous pouvez également associer une chaîne d'aide spécifique à un autre contrôle au moyen de la méthode <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>.  La chaîne que vous associez à un contrôle en vous servant de cette méthode vient s'afficher dans une fenêtre indépendante quand l'utilisateur appuie sur la touche F1 alors que le contrôle a le focus.  
  
 Si <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> n'a pas été défini, vous devez utiliser <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> pour fournir le texte d'aide.  Si vous avez défini <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> et la chaîne d'aide, l'aide de <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> prévaut.  
  
> [!NOTE]
>  Des incidents risquent de survenir lorsque vous utilisez le chemin d'accès relatif pour spécifier le chemin d'accès au fichier d'aide dans la méthode <xref:System.Windows.Forms.Help.ShowHelp%2A> ou dans la propriété <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> du contrôle <xref:System.Windows.Forms.HelpProvider>.  C'est la raison pour laquelle vous devez veiller à utiliser le chemin d'accès absolu du fichier d'aide.  
  
## Voir aussi  
 [Systèmes d'aide dans les applications Windows Forms](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)