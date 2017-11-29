---
title: Vue d'ensemble des graphismes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0a3286cbcaa0eebf59500582a749804b5e1b8ba
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="overview-of-graphics"></a><span data-ttu-id="de834-102">Vue d'ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="de834-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="de834-103">est une interface de programmation d’applications (API) qui forme le sous-système du système d’exploitation Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="de834-103"> is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="de834-104">est responsable de l’affichage des informations sur les écrans et les imprimantes.</span><span class="sxs-lookup"><span data-stu-id="de834-104"> is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="de834-105">Comme son nom le suggère, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est le successeur de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], l'interface GDI (Graphics Device Interface) fournie avec les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="de834-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="de834-106">Interface de classes managées</span><span class="sxs-lookup"><span data-stu-id="de834-106">Managed Class Interface</span></span>  
 <span data-ttu-id="de834-107">Le [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API est exposée via un ensemble de classes déployées comme du code managé.</span><span class="sxs-lookup"><span data-stu-id="de834-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="de834-108">Cet ensemble de classes est appelé le *interface de classes managées* à [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de834-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="de834-109">Les espaces de noms suivants composent l'interface de classes managées :</span><span class="sxs-lookup"><span data-stu-id="de834-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="de834-110">Avec une Interface graphique, tels que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez afficher des informations sur un écran ou une imprimante sans avoir à se soucier des détails d’un périphérique d’affichage particulier.</span><span class="sxs-lookup"><span data-stu-id="de834-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="de834-111">Le programmeur effectue des appels aux méthodes fournies par les classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de834-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="de834-112">Ces méthodes effectuent ensuite les appels appropriés aux pilotes de périphériques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="de834-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="de834-113"> isole l'application du matériel graphique.</span><span class="sxs-lookup"><span data-stu-id="de834-113"> insulates the application from the graphics hardware.</span></span> <span data-ttu-id="de834-114">C’est cette isolation qui permet à un programmeur de créer des applications indépendantes du périphérique.</span><span class="sxs-lookup"><span data-stu-id="de834-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de834-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de834-115">See Also</span></span>  
 [<span data-ttu-id="de834-116">Vue d’ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="de834-116">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
