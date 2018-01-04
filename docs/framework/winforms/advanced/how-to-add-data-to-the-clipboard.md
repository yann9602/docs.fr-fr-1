---
title: "Comment : ajouter des données au Presse-papiers"
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
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 452dfc5a9645e8f43ab583099deec60faa2d1b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="6bc4c-102">Comment : ajouter des données au Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="6bc4c-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="6bc4c-103">La <xref:System.Windows.Forms.Clipboard> classe fournit des méthodes que vous pouvez utiliser pour interagir avec la fonctionnalité du Presse-papiers du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="6bc4c-104">De nombreuses applications utilisent le Presse-papiers comme référentiel temporaire pour les données.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="6bc4c-105">Par exemple, les traitements utiliser le Presse-papiers lors des opérations de couper-coller.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="6bc4c-106">Le Presse-papiers est également utile pour transférer des données d’une application vers un autre.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="6bc4c-107">Lorsque vous ajoutez des données dans le Presse-papiers, vous pouvez indiquer le format de données afin que les autres applications puissent reconnaître les données lorsqu’elles peuvent utiliser ce format.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="6bc4c-108">Vous pouvez également ajouter des données dans le Presse-papiers dans plusieurs formats différents pour augmenter le nombre d’autres applications qui peut utiliser les données.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="6bc4c-109">Un format de Presse-papiers est une chaîne qui identifie le format afin qu’une application qui utilise ce format puisse récupérer les données associées.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="6bc4c-110">La <xref:System.Windows.Forms.DataFormats> classe fournit les noms de formats prédéfinis pour votre utilisation.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="6bc4c-111">Vous pouvez également utiliser vos propres noms de format ou utilisez le type d’un objet comme son format.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="6bc4c-112">Pour ajouter des données dans le Presse-papiers dans un ou plusieurs formats, utilisez le <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6bc4c-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="6bc4c-113">Vous pouvez passer n’importe quel objet à cette méthode, mais pour ajouter des données dans plusieurs formats, vous devez d’abord ajouter les données à un objet distinct conçu pour fonctionner avec plusieurs formats.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="6bc4c-114">En règle générale, vous allez ajouter vos données à un <xref:System.Windows.Forms.DataObject>, mais vous pouvez utiliser n’importe quel type qui implémente le <xref:System.Windows.Forms.IDataObject> interface.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="6bc4c-115">Dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], vous pouvez ajouter des données directement dans le Presse-papiers à l’aide de nouvelles méthodes conçues pour simplifier les tâches de base du Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="6bc4c-116">Utilisez ces méthodes lorsque vous travaillez avec des données dans un format commun, telles que du texte.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bc4c-117">Toutes les applications Windows partagent le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="6bc4c-118">Par conséquent, le contenu est susceptible de changer lorsque vous basculez vers une autre application.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="6bc4c-119">La <xref:System.Windows.Forms.Clipboard> classe peut uniquement être utilisée dans les threads en mode thread unique cloisonné (STA).</span><span class="sxs-lookup"><span data-stu-id="6bc4c-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="6bc4c-120">Pour utiliser cette classe, assurez-vous que votre `Main` méthode est marquée avec le <xref:System.STAThreadAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="6bc4c-121">Un objet doit être sérialisable pour pouvoir être placé dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="6bc4c-122">Pour rendre un type sérialisable, marquez-le avec le <xref:System.SerializableAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="6bc4c-123">Si vous passez un objet non sérialisable à une méthode du Presse-papiers, la méthode échoue sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="6bc4c-124">Pour plus d'informations sur la sérialisation, consultez <xref:System.Runtime.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="6bc4c-125">Pour ajouter des données dans le Presse-papiers dans un format commun unique</span><span class="sxs-lookup"><span data-stu-id="6bc4c-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="6bc4c-126">Utilisez le <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.SetText%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6bc4c-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="6bc4c-127">Ces méthodes sont disponibles uniquement dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bc4c-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="6bc4c-128">Pour ajouter des données dans le Presse-papiers dans un format personnalisé</span><span class="sxs-lookup"><span data-stu-id="6bc4c-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="6bc4c-129">Utilisez la <xref:System.Windows.Forms.Clipboard.SetData%2A> méthode avec un nom de format personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="6bc4c-130">Cette méthode est uniquement disponible dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bc4c-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="6bc4c-131">Vous pouvez également utiliser des noms de formats prédéfinis avec la <xref:System.Windows.Forms.Clipboard.SetData%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6bc4c-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="6bc4c-132">Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="6bc4c-133">Pour ajouter des données dans le Presse-papiers dans plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="6bc4c-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="6bc4c-134">Utilisez le <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> (méthode) et passez un <xref:System.Windows.Forms.DataObject> qui contient vos données.</span><span class="sxs-lookup"><span data-stu-id="6bc4c-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="6bc4c-135">Vous devez utiliser cette méthode pour ajouter des données dans le Presse-papiers dans les versions antérieures à [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bc4c-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="6bc4c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bc4c-136">See Also</span></span>  
 [<span data-ttu-id="6bc4c-137">Opérations glisser-déposer et prise en charge du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="6bc4c-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="6bc4c-138">Guide pratique pour récupérer des données du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="6bc4c-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
