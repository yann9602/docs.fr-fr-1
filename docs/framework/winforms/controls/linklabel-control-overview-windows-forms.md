---
title: "Vue d'ensemble du contrôle LinkLabel (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0cb01c0fc5503a5bf16e1f191d87ae90907ec816
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linklabel-control-overview-windows-forms"></a>Vue d'ensemble du contrôle LinkLabel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> contrôle vous permet d’ajouter des liens Web dans les applications Windows Forms. Vous pouvez utiliser la <xref:System.Windows.Forms.LinkLabel> contrôle pour tous les éléments que vous pouvez utiliser le <xref:System.Windows.Forms.Label> de contrôle pour ; vous pouvez également définir une partie du texte sous forme de lien vers un fichier, un dossier ou une page Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Ce que vous pouvez faire avec le contrôle LinkLabel  
 En plus de toutes les propriétés, méthodes et événements de la <xref:System.Windows.Forms.Label> (contrôle), le <xref:System.Windows.Forms.LinkLabel> contrôle possède des propriétés pour les liens hypertexte et les couleurs de liaison. Le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété définit la zone de texte qui active la liaison. Le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, et <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> propriétés définissent les couleurs de la liaison. Le <xref:System.Windows.Forms.LinkLabel.LinkClicked> événement détermine ce qui se passe lorsque le texte du lien est sélectionné.  
  
 L’utilisation la plus simple de la <xref:System.Windows.Forms.LinkLabel> contrôle consiste à afficher un lien unique à l’aide de la <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété, mais vous pouvez également afficher plusieurs liens hypertexte à l’aide de la <xref:System.Windows.Forms.LinkLabel.Links%2A> propriété. Le <xref:System.Windows.Forms.LinkLabel.Links%2A> propriété permet d’accéder à une collection de liens. Vous pouvez également spécifier des données dans le <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriété individuelle de chaque <xref:System.Windows.Forms.LinkLabel.Link> objet. La valeur de la <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriété peut être utilisée pour stocker l’emplacement d’un fichier à l’affichage ou l’adresse d’un site Web.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.LinkLabel>  
 [Vue d'ensemble du contrôle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
