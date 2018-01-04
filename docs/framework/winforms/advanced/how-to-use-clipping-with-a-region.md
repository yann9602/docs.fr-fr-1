---
title: "Comment : utiliser le découpage avec une région"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 281ae701bc3e5cee38952a05474360019f76a665
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="2f3d5-102">Comment : utiliser le découpage avec une région</span><span class="sxs-lookup"><span data-stu-id="2f3d5-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="2f3d5-103">Une des propriétés de la <xref:System.Drawing.Graphics> classe est la zone de découpage.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="2f3d5-104">Tout le dessin effectué un donné <xref:System.Drawing.Graphics> objet est limité à la zone de découpage de ce <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="2f3d5-105">Vous pouvez définir la zone de découpage en appelant le <xref:System.Drawing.Graphics.SetClip%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="2f3d5-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f3d5-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f3d5-106">Example</span></span>  
 <span data-ttu-id="2f3d5-107">L’exemple suivant construit un chemin d’accès qui se compose d’un polygone unique.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="2f3d5-108">Le code crée ensuite une région, en fonction de ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="2f3d5-109">La région est passée à la <xref:System.Drawing.Graphics.SetClip%2A> méthode d’un <xref:System.Drawing.Graphics> objet, puis les deux chaînes sont dessinées.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="2f3d5-110">L’illustration suivante montre les chaînes découpées.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="2f3d5-111">![Élément](../../../../docs/framework/winforms/advanced/media/clip1.png "1 sur")</span><span class="sxs-lookup"><span data-stu-id="2f3d5-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f3d5-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2f3d5-112">Compiling the Code</span></span>  
 <span data-ttu-id="2f3d5-113">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="2f3d5-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3d5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f3d5-114">See Also</span></span>  
 [<span data-ttu-id="2f3d5-115">Régions dans GDI+</span><span class="sxs-lookup"><span data-stu-id="2f3d5-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="2f3d5-116">Utilisation de régions</span><span class="sxs-lookup"><span data-stu-id="2f3d5-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
