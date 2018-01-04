---
title: "Comment : récupérer des données dans un format de données particulier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 884b017a69e55cfccc9201ad2d101017b0c290b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="7778c-102">Comment : récupérer des données dans un format de données particulier</span><span class="sxs-lookup"><span data-stu-id="7778c-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="7778c-103">Les exemples suivants montrent comment récupérer des données à partir d’un objet de données dans un format spécifié.</span><span class="sxs-lookup"><span data-stu-id="7778c-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7778c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7778c-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7778c-105">Description</span><span class="sxs-lookup"><span data-stu-id="7778c-105">Description</span></span>  
 <span data-ttu-id="7778c-106">L’exemple de code suivant utilise la <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> surcharge vérifier d’abord si format de données spécifiée est disponible (en mode natif ou par conversion automatique) ; si le format spécifié est disponible, l’exemple récupère les données à l’aide de la <xref:System.Windows.DataObject.GetData%28System.String%29> (méthode).</span><span class="sxs-lookup"><span data-stu-id="7778c-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7778c-107">Code</span><span class="sxs-lookup"><span data-stu-id="7778c-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="7778c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="7778c-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7778c-109">Description</span><span class="sxs-lookup"><span data-stu-id="7778c-109">Description</span></span>  
 <span data-ttu-id="7778c-110">L’exemple de code suivant utilise la <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> surcharge vérifier d’abord si un format de données spécifié est disponible en mode natif (les formats de données convertibles automatiquement sont filtrés) ; si le format spécifié est disponible, l’exemple récupère les données à l’aide de la <xref:System.Windows.DataObject.GetData%28System.String%29>(méthode).</span><span class="sxs-lookup"><span data-stu-id="7778c-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7778c-111">Code</span><span class="sxs-lookup"><span data-stu-id="7778c-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="7778c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7778c-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="7778c-113">Vue d'ensemble du glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="7778c-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
