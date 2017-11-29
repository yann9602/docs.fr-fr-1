---
title: Utilisation de conteneurs graphiques
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 337057e10e03712aa93b00d9c687374e53f8dd03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="63aa2-102">Utilisation de conteneurs graphiques</span><span class="sxs-lookup"><span data-stu-id="63aa2-102">Using Graphics Containers</span></span>
<span data-ttu-id="63aa2-103">A <xref:System.Drawing.Graphics> objet fournit des méthodes telles que <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, et <xref:System.Drawing.Graphics.DrawString%2A> pour l’affichage des images vectorielles, des images raster et texte.</span><span class="sxs-lookup"><span data-stu-id="63aa2-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="63aa2-104">A <xref:System.Drawing.Graphics> objet possède également plusieurs propriétés qui influencent la qualité et l’orientation des éléments qui sont dessinées.</span><span class="sxs-lookup"><span data-stu-id="63aa2-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="63aa2-105">Par exemple, la propriété du mode de lissage détermine si l’anticrénelage est appliquée à des lignes et des courbes, et la propriété de transformation universelle influence sur la position et la rotation des éléments qui sont dessinées.</span><span class="sxs-lookup"><span data-stu-id="63aa2-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="63aa2-106">A <xref:System.Drawing.Graphics> objet est associé à un périphérique d’affichage particulier.</span><span class="sxs-lookup"><span data-stu-id="63aa2-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="63aa2-107">Lorsque vous utilisez un <xref:System.Drawing.Graphics> objet à dessiner dans une fenêtre, le <xref:System.Drawing.Graphics> objet est également associé à cette fenêtre particulière.</span><span class="sxs-lookup"><span data-stu-id="63aa2-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="63aa2-108">A <xref:System.Drawing.Graphics> objet peut être considéré comme un conteneur car il conserve un jeu de propriétés qui influencent le dessin et il est lié à des informations spécifiques au périphérique.</span><span class="sxs-lookup"><span data-stu-id="63aa2-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="63aa2-109">Vous pouvez créer un conteneur secondaire dans un fichier <xref:System.Drawing.Graphics> objet en appelant le <xref:System.Drawing.Graphics.BeginContainer%2A> méthode qui <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="63aa2-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63aa2-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="63aa2-110">In This Section</span></span>  
 [<span data-ttu-id="63aa2-111">Gestion de l'état d'un objet graphique</span><span class="sxs-lookup"><span data-stu-id="63aa2-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="63aa2-112">Décrit comment gérer les paramètres de qualité, zone de découpage et les transformations d’une <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="63aa2-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="63aa2-113">Utilisation de conteneurs graphiques imbriqués</span><span class="sxs-lookup"><span data-stu-id="63aa2-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="63aa2-114">Montre comment utiliser des conteneurs pour contrôler l’état de la <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="63aa2-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
