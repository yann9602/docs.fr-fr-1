---
title: "Coordonnées Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="8802a-102">Coordonnées Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8802a-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="8802a-103">Le système de coordonnées pour un Windows Form est basé sur les coordonnées de périphérique, et l’unité de mesure lors du dessin dans les Windows Forms de base est l’unité de périphérique (en général, le pixel).</span><span class="sxs-lookup"><span data-stu-id="8802a-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="8802a-104">Points à l’écran sont décrits par des paires de coordonnées x et y, avec les coordonnées x qui augmentent vers la droite et les coordonnées y augmentant de haut en bas.</span><span class="sxs-lookup"><span data-stu-id="8802a-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="8802a-105">L’emplacement de l’origine, par rapport à l’écran, varient selon que vous spécifiez les coordonnées d’écran ou un client.</span><span class="sxs-lookup"><span data-stu-id="8802a-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="8802a-106">Coordonnées d’écran</span><span class="sxs-lookup"><span data-stu-id="8802a-106">Screen Coordinates</span></span>  
 <span data-ttu-id="8802a-107">Une application Windows Forms spécifie la position d’une fenêtre à l’écran en coordonnées d’écran.</span><span class="sxs-lookup"><span data-stu-id="8802a-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="8802a-108">Pour les coordonnées d’écran, l’origine sont l’angle supérieur gauche de l’écran.</span><span class="sxs-lookup"><span data-stu-id="8802a-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="8802a-109">La position complète d’une fenêtre est souvent décrite par un <xref:System.Drawing.Rectangle> structure qui contient les coordonnées d’écran de deux points qui définissent les angles supérieur gauche et à droite de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="8802a-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="8802a-110">Coordonnées clientes</span><span class="sxs-lookup"><span data-stu-id="8802a-110">Client Coordinates</span></span>  
 <span data-ttu-id="8802a-111">Une application Windows Forms spécifie la position des points dans un formulaire ou un contrôle à l’aide de coordonnées clientes.</span><span class="sxs-lookup"><span data-stu-id="8802a-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="8802a-112">L’origine pour les coordonnées clientes est l’angle supérieur gauche de la zone cliente du contrôle ou du formulaire.</span><span class="sxs-lookup"><span data-stu-id="8802a-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="8802a-113">Les coordonnées clientes garantissent qu’une application peut utiliser des valeurs de coordonnée cohérentes en dessinant dans un formulaire ou un contrôle, indépendamment de la position du formulaire ou contrôle sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="8802a-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="8802a-114">Les dimensions de la zone cliente sont également décrites par un <xref:System.Drawing.Rectangle> structure qui contient les coordonnées clientes pour la zone.</span><span class="sxs-lookup"><span data-stu-id="8802a-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="8802a-115">Dans tous les cas, les coordonnées du coin supérieur gauche du rectangle sont incluses dans la zone cliente, alors que la coordonnée inférieur droit est exclue.</span><span class="sxs-lookup"><span data-stu-id="8802a-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="8802a-116">Opérations graphiques n’incluent pas les bords droit et inférieurs d’une zone cliente.</span><span class="sxs-lookup"><span data-stu-id="8802a-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="8802a-117">Par exemple le <xref:System.Drawing.Graphics.FillRectangle%2A> méthode arrive à saturation et le bord droit et inférieur du rectangle spécifié, mais n’inclura pas ces bords.</span><span class="sxs-lookup"><span data-stu-id="8802a-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="8802a-118">Mappage d’un Type de coordonnées à un autre</span><span class="sxs-lookup"><span data-stu-id="8802a-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="8802a-119">Parfois, vous devrez peut-être mapper des coordonnées d’écran en coordonnées clientes.</span><span class="sxs-lookup"><span data-stu-id="8802a-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="8802a-120">Vous pouvez le faire facilement à l’aide de la <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> méthodes disponibles dans la <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="8802a-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="8802a-121">Par exemple, le <xref:System.Windows.Forms.Control.MousePosition%2A> propriété du <xref:System.Windows.Forms.Control> est signalée en coordonnées d’écran, mais vous pouvez convertir celles-ci en coordonnées clientes.</span><span class="sxs-lookup"><span data-stu-id="8802a-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8802a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8802a-122">See Also</span></span>  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
