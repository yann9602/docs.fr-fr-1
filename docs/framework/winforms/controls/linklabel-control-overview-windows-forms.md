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
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="b12e0-102">Vue d'ensemble du contrôle LinkLabel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b12e0-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="b12e0-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> contrôle vous permet d’ajouter des liens Web dans les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b12e0-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="b12e0-104">Vous pouvez utiliser la <xref:System.Windows.Forms.LinkLabel> contrôle pour tous les éléments que vous pouvez utiliser le <xref:System.Windows.Forms.Label> de contrôle pour ; vous pouvez également définir une partie du texte sous forme de lien vers un fichier, un dossier ou une page Web.</span><span class="sxs-lookup"><span data-stu-id="b12e0-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="b12e0-105">Ce que vous pouvez faire avec le contrôle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b12e0-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="b12e0-106">En plus de toutes les propriétés, méthodes et événements de la <xref:System.Windows.Forms.Label> (contrôle), le <xref:System.Windows.Forms.LinkLabel> contrôle possède des propriétés pour les liens hypertexte et les couleurs de liaison.</span><span class="sxs-lookup"><span data-stu-id="b12e0-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="b12e0-107">Le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété définit la zone de texte qui active la liaison.</span><span class="sxs-lookup"><span data-stu-id="b12e0-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="b12e0-108">Le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, et <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> propriétés définissent les couleurs de la liaison.</span><span class="sxs-lookup"><span data-stu-id="b12e0-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="b12e0-109">Le <xref:System.Windows.Forms.LinkLabel.LinkClicked> événement détermine ce qui se passe lorsque le texte du lien est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b12e0-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="b12e0-110">L’utilisation la plus simple de la <xref:System.Windows.Forms.LinkLabel> contrôle consiste à afficher un lien unique à l’aide de la <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété, mais vous pouvez également afficher plusieurs liens hypertexte à l’aide de la <xref:System.Windows.Forms.LinkLabel.Links%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b12e0-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="b12e0-111">Le <xref:System.Windows.Forms.LinkLabel.Links%2A> propriété permet d’accéder à une collection de liens.</span><span class="sxs-lookup"><span data-stu-id="b12e0-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="b12e0-112">Vous pouvez également spécifier des données dans le <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriété individuelle de chaque <xref:System.Windows.Forms.LinkLabel.Link> objet.</span><span class="sxs-lookup"><span data-stu-id="b12e0-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="b12e0-113">La valeur de la <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriété peut être utilisée pour stocker l’emplacement d’un fichier à l’affichage ou l’adresse d’un site Web.</span><span class="sxs-lookup"><span data-stu-id="b12e0-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12e0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12e0-114">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="b12e0-115">Vue d'ensemble du contrôle Label</span><span class="sxs-lookup"><span data-stu-id="b12e0-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="b12e0-116">Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b12e0-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="b12e0-117">Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b12e0-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
