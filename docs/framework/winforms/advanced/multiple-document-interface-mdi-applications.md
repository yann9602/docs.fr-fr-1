---
title: "Applications d&#39;interface multidocument (MDI, Multiple Document Interface) | Microsoft Docs"
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
  - "formulaires, MDI"
  - "MDI"
  - "Windows Forms, applications MDI"
  - "fenêtres, MDI"
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Applications d&#39;interface multidocument (MDI, Multiple Document Interface)
Les applications d'interface multidocument \(MDI\) vous permettent d'afficher simultanément plusieurs documents, chacun dans une fenêtre différente.  Les applications MDI comportent souvent un élément de menu Fenêtre contenant des sous\-menus qui permettent de passer d'une fenêtre ou d'un document à un autre.  
  
> [!NOTE]
>  Il existe quelques différences entre le comportement des formulaires MDI et celui des fenêtres d'interface monodocument \(SDI, Single Document Interface\) dans les Windows Forms.  La propriété `Opacity` n'a aucun impact sur l'apparence des formulaires MDI enfants.  En outre, la méthode <xref:System.Windows.Forms.Form.CenterToParent%2A> n'affecte pas leur comportement.  
  
## Dans cette section  
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 Explique comment créer le conteneur de plusieurs documents dans une application MDI.  
  
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 Explique comment créer une ou plusieurs fenêtres opérant dans un formulaire MDI parent.  
  
 [Comment : déterminer l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 Explique comment déterminer la fenêtre enfant qui a le focus \(et envoyer son contenu vers le Presse\-papiers\).  
  
 [Comment : envoyer des données à l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 Explique comment transmettre des informations à la fenêtre enfant active.  
  
 [Comment : réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 Explique comment afficher les fenêtres enfants d'une application MDI en mosaïque ou en cascade, et comment les réorganiser.