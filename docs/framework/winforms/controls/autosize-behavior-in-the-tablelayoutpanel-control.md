---
title: "Comportement du redimensionnement automatique dans le contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="3c7c3-102">Comportement du redimensionnement automatique dans le contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3c7c3-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="3c7c3-103">Comportements de redimensionnement automatique distincts</span><span class="sxs-lookup"><span data-stu-id="3c7c3-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="3c7c3-104">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle prend en charge le comportement de dimensionnement automatique des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c7c3-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="3c7c3-105">Via le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété ;</span><span class="sxs-lookup"><span data-stu-id="3c7c3-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="3c7c3-106">Via le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété sur le <xref:System.Windows.Forms.TableLayoutPanel> les styles de ligne et de colonne du contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="3c7c3-107">La propriété AutoSize avec les Styles de colonne et de ligne</span><span class="sxs-lookup"><span data-stu-id="3c7c3-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="3c7c3-108">Le tableau suivant décrit l’interaction entre le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété et la <xref:System.Windows.Forms.TableLayoutPanel> les styles de ligne et de colonne du contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="3c7c3-109">Paramètre de redimensionnement automatique</span><span class="sxs-lookup"><span data-stu-id="3c7c3-109">AutoSize setting</span></span>|<span data-ttu-id="3c7c3-110">Interaction de style</span><span class="sxs-lookup"><span data-stu-id="3c7c3-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="3c7c3-111">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle opère de gauche à droite et alloue de l’espace pour la colonne ou la ligne ou dans l’ordre suivant.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="3c7c3-112">1.  Si le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> est définie sur <xref:System.Windows.Forms.SizeType.Absolute>, le nombre de pixels spécifié par <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> est allouée.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="3c7c3-113">2.  Si le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> est définie sur <xref:System.Windows.Forms.SizeType.AutoSize>, le nombre de pixels retourné par le contrôle d’enfant <xref:System.Windows.Forms.Control.GetPreferredSize%2A> (méthode) est allouée.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="3c7c3-114">3.  Après l’espace pour toutes les <xref:System.Windows.Forms.SizeType.Absolute> et <xref:System.Windows.Forms.SizeType.AutoSize> les colonnes ou lignes est alloué, des colonnes ou des lignes avec <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> la valeur <xref:System.Windows.Forms.SizeType.Percent> sont utilisées pour allouer l’espace libre restant proportionnellement</span><span class="sxs-lookup"><span data-stu-id="3c7c3-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="3c7c3-115">Semblable à l’interaction précédente, avec l’exception qui <xref:System.Windows.Forms.SizeType.Percent> les colonnes ou lignes acquièrent un aspect de dimensionnement automatique.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="3c7c3-116">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle développe la colonne ou ligne pour créer un espace adéquat, afin qu’aucune colonne ou ligne avec <xref:System.Windows.Forms.SizeType.Percent> style découpe son contenu.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="3c7c3-117">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle alloue le nouvel espace proportionnellement en fonction de la <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="3c7c3-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c7c3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c7c3-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="3c7c3-119">Vue d’ensemble du contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3c7c3-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
