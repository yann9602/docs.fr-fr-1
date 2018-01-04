---
title: "Utilisation du modèle objet de document HTML managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 876cee67f917291214d6ea8b9abf7d2975c1fd25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="6ad52-102">Utilisation du modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="6ad52-103">Le modèle d’objet document HTML managé (DOM) fournit un wrapper basé sur le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour les classes HTML exposées par Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6ad52-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="6ad52-104">Utilisez ces classes pour manipuler des pages HTML hébergées dans le <xref:System.Windows.Forms.WebBrowser> (contrôle), ou pour créer de nouvelles pages à partir du début.</span><span class="sxs-lookup"><span data-stu-id="6ad52-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ad52-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6ad52-105">In This Section</span></span>  
 [<span data-ttu-id="6ad52-106">Guide pratique pour accéder au modèle DOM (Document Object Model) HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6ad52-107">Décrit comment obtenir une instance valide de <xref:System.Windows.Forms.HtmlDocument> à partir d’une application Windows Forms ou un <xref:System.Windows.Forms.UserControl> hébergée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6ad52-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="6ad52-108">Guide pratique pour accéder à la source HTML dans le modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6ad52-109">Décrit comment obtenir la source HTML d’origine, non modifiée et comment obtenir la source « dynamique » qui reflète l’état actuel du DOM.</span><span class="sxs-lookup"><span data-stu-id="6ad52-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="6ad52-110">Guide pratique pour modifier des styles d'un élément dans le modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6ad52-111">Explique comment manipuler les styles, qui sont utilisés pour contrôler l’affichage d’éléments.</span><span class="sxs-lookup"><span data-stu-id="6ad52-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="6ad52-112">Accès aux frames dans le modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6ad52-113">Décrit ce qu’est les cadres et des jeux de frames et comment accéder au DOM d’un frame.</span><span class="sxs-lookup"><span data-stu-id="6ad52-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="6ad52-114">Accès aux membres non exposés sur le modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="6ad52-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6ad52-115">Décrit comment accéder aux membres du modèle DOM sous-jacent qui n’ont pas d’équivalent managé.</span><span class="sxs-lookup"><span data-stu-id="6ad52-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ad52-116">Référence</span><span class="sxs-lookup"><span data-stu-id="6ad52-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="6ad52-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6ad52-117">Related Sections</span></span>  
 [<span data-ttu-id="6ad52-118">WebBrowser, contrôle</span><span class="sxs-lookup"><span data-stu-id="6ad52-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ad52-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ad52-119">See Also</span></span>  
 [<span data-ttu-id="6ad52-120">Sur le modèle d’objet DHTML</span><span class="sxs-lookup"><span data-stu-id="6ad52-120">About the DHTML Object Model</span></span>](http://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
