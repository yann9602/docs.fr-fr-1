---
title: "Vue d&#39;ensemble du composant ErrorProvider (Windows Forms) | Microsoft Docs"
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
  - "ErrorProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "messages d'erreur, afficher"
  - "ErrorProvider (composant Windows Forms), à propos du composant ErrorProvider"
  - "erreurs (Windows Forms), afficher aux utilisateurs"
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble du composant ErrorProvider (Windows Forms)
Le composant [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) Windows Forms est utilisé pour valider les entrées d'utilisateur dans un formulaire ou dans un contrôle.  Il est en général utilisé avec la validation des données entrées par l'utilisateur dans un formulaire ou avec l'affichage des erreurs dans un groupe de données.  Un fournisseur d'erreur constitue une meilleure alternative que l'affichage d'un message d'erreur dans une boîte de message, parce que cette dernière n'est plus visible lorsque le message est fermé.  Le composant <xref:System.Windows.Forms.ErrorProvider> affiche une icône d'erreur \(![Icône ErrorProvider](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.png "vbErrorProviderIcon")\) en regard du contrôle concerné \(zone de texte, par exemple\) ; lorsque l'utilisateur positionne le pointeur de la souris sur cette icône, une info\-bulle apparaît et affiche le message d'erreur.  
  
## Propriétés de clé  
 Les propriétés principales du composant <xref:System.Windows.Forms.ErrorProvider> sont <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> et <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.  Lorsque vous utilisez le composant <xref:System.Windows.Forms.ErrorProvider> avec des contrôles liés aux données, la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> doit être définie avec le conteneur approprié \(en général Windows Form\) pour que le composant affiche une icône d'erreur dans le formulaire.  Lorsque le composant est ajouté dans le concepteur, la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> est définie avec le formulaire conteneur ; si vous ajoutez le contrôle dans du code, vous devez la définir vous\-même.  
  
 Vous pouvez définir pour la propriété <xref:System.Windows.Forms.ErrorProvider.Icon%2A> une icône d'erreur personnalisée en remplacement de celle par défaut.  Lorsque la propriété <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> est définie, le composant <xref:System.Windows.Forms.ErrorProvider> peut afficher des messages d'erreur pour un groupe de données.  La principale méthode du composant <xref:System.Windows.Forms.ErrorProvider> est <xref:System.Windows.Forms.ErrorProvider.SetError%2A>, qui spécifie le message d'erreur et l'endroit où l'icône d'erreur doit s'afficher.  
  
> [!NOTE]
>  Le composant <xref:System.Windows.Forms.ErrorProvider> ne fournit pas d'assistance intégrée pour les clients d'accessibilité.  Pour rendre votre application accessible lors de votre utilisation de ce composant, vous devez fournir un mécanisme de commentaires supplémentaire, accessible.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ErrorProvider>   
 [Comment : afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)   
 [Comment : afficher des icônes d'erreur pour la validation de formulaire à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)