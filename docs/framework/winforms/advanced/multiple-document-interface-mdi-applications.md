---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c122931b0a00f487ddab07550913988462cfd50e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a>Applications d'interface multidocument (MDI, Multiple Document Interface)
Applications d’interface multidocument (MDI) permettent d’afficher plusieurs documents en même temps, chaque document affiché dans sa propre fenêtre. Les applications MDI ont souvent un élément de menu Fenêtre avec les sous-menus de basculer entre les fenêtres et aux documents.  
  
> [!NOTE]
>  Il existe des différences de comportement entre des formulaires MDI et les fenêtres de l’interface monodocument (SDI) dans les Windows Forms. Le `Opacity` propriété n’affecte pas l’apparence des formulaires MDI enfants. En outre, le <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires MDI enfants.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 Explique comment créer le conteneur de plusieurs documents dans une application MDI.  
  
 [Guide pratique pour créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 Fournit des instructions pour la création d’une ou plusieurs fenêtres qui opèrent dans un formulaire MDI parent.  
  
 [Guide pratique pour déterminer l’enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 Fournit des instructions pour la vérification de la fenêtre enfant qui a le focus (et envoyer son contenu dans le Presse-papiers).  
  
 [Guide pratique pour envoyer des données à l’enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 Explique comment transmettre des informations à la fenêtre enfant active.  
  
 [Guide pratique pour réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 Fournit des instructions pour la disposition en mosaïque, en cascade ou réorganiser les fenêtres enfants d’une application MDI.
