---
title: "Opérations glisser-déposer et prise en charge du Presse-papiers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27ba3e94e28a1e26d370fa6daf7c93019d1e2428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="03485-102">Opérations glisser-déposer et prise en charge du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="03485-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="03485-103">Vous pouvez activer les opérations de glisser-déplacer dans une application Windows en gérant une série d'événements, notamment <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, et <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="03485-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="03485-104">Vous pouvez aussi implémenter la prise en charge des opérations couper/copier/coller par l'utilisateur et le transfert de données par l'utilisateur dans le Presse-papiers dans vos applications Windows à l'aide de simples appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="03485-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03485-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="03485-105">In This Section</span></span>  
 [<span data-ttu-id="03485-106">Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03485-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="03485-107">Explique comment démarrer une opération de glisser-déposer.</span><span class="sxs-lookup"><span data-stu-id="03485-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="03485-108">Guide pratique pour exécuter des opérations de glisser-déposer entre des applications</span><span class="sxs-lookup"><span data-stu-id="03485-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="03485-109">Montre comment effectuer des opérations de glisser-déposer entre des applications.</span><span class="sxs-lookup"><span data-stu-id="03485-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="03485-110">Guide pratique pour ajouter des données au Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="03485-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="03485-111">Décrit un moyen d'insérer des informations dans le Presse-papiers par programmation.</span><span class="sxs-lookup"><span data-stu-id="03485-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="03485-112">Guide pratique pour récupérer des données du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="03485-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="03485-113">Décrit comment accéder aux données stockées dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="03485-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="03485-114">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="03485-114">Related Sections</span></span>  
 [<span data-ttu-id="03485-115">Fonctionnalité de glisser-déposer dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03485-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="03485-116">Décrit les méthodes, les événements et les classes utilisés pour implémenter le comportement de glisser-déposer.</span><span class="sxs-lookup"><span data-stu-id="03485-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="03485-117">Décrit les complexités de l'événement qui demande l'autorisation de continuer l'opération glisser.</span><span class="sxs-lookup"><span data-stu-id="03485-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="03485-118">Décrit les complexités de la méthode qui est centrale au démarrage d'une opération glisser.</span><span class="sxs-lookup"><span data-stu-id="03485-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="03485-119">Consultez également [Comment : envoyer des données à l’enfant MDI actif](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="03485-119">Also see [How to: Send Data to the Active MDI Child](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>
