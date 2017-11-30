---
title: "Comment : valider et fusionner des PrintTicket"
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
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c2929f37895f0dee5529a5bf90f84146585032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="e1c9a-102">Comment : valider et fusionner des PrintTicket</span><span class="sxs-lookup"><span data-stu-id="e1c9a-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="e1c9a-103">Le [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [schéma d’impression](http://go.microsoft.com/fwlink/?LinkId=186397) inclut flexible et extensible <xref:System.Printing.PrintCapabilities> et <xref:System.Printing.PrintTicket> éléments.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="e1c9a-104">Le premier comptabilise les fonctions d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités par rapport à une séquence particulière de documents, de document individuel ou de page individuelle.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="e1c9a-105">Une séquence standard de tâches pour une application qui prend en charge l’impression serait comme suit.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="e1c9a-106">Déterminer les fonctionnalités d’une imprimante.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="e1c9a-107">Configurer un <xref:System.Printing.PrintTicket> pour utiliser ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="e1c9a-108">Valider la <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="e1c9a-109">Cet article explique comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1c9a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1c9a-110">Example</span></span>  
 <span data-ttu-id="e1c9a-111">Dans l’exemple ci-dessous, nous sommes intéressés uniquement si une imprimante peut prendre en charge : impression recto-verso.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="e1c9a-112">Les étapes principales sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="e1c9a-113">Obtenir un <xref:System.Printing.PrintCapabilities> de l’objet avec le <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e1c9a-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="e1c9a-114">Tester la présence de la fonctionnalité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="e1c9a-115">Dans l’exemple ci-dessous, nous testons la <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriété de la <xref:System.Printing.PrintCapabilities> la présence de la fonction d’impression sur les deux côtés d’une feuille de papier, la rotation de « page » de l’objet le long du côté long de la feuille.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="e1c9a-116">Étant donné que <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> est une collection, nous utilisons le `Contains` méthode <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1c9a-117">Cette étape n’est pas strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-117">This step is not strictly necessary.</span></span> <span data-ttu-id="e1c9a-118">Le <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> méthode utilisée ci-dessous vérifiera chaque demande le <xref:System.Printing.PrintTicket> aux capacités de l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="e1c9a-119">Si la fonction demandée n’est pas pris en charge par l’imprimante, le pilote d’imprimante substituera une autre demande dans le <xref:System.Printing.PrintTicket> retourné par la méthode.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="e1c9a-120">Si l’imprimante prend en charge l’impression recto verso, l’exemple de code crée un <xref:System.Printing.PrintTicket> qui demande la duplication.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="e1c9a-121">Mais l’application ne spécifie pas de chaque paramètre disponible dans l’imprimante possible la <xref:System.Printing.PrintTicket> élément.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="e1c9a-122">Ce serait une perte de programmeur et durée du programme.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="e1c9a-123">Au lieu de cela, le code définit uniquement la demande d’impression recto verso et puis fusionne ce <xref:System.Printing.PrintTicket> avec un existant, entièrement configuré et validé, <xref:System.Printing.PrintTicket>, dans ce cas, par défaut de l’utilisateur <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="e1c9a-124">En conséquence, l’exemple appelle la <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> à fusionner la nouvelle méthode minimal, <xref:System.Printing.PrintTicket> avec la valeur par défaut de l’utilisateur <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="e1c9a-125">Cette opération retourne un <xref:System.Printing.ValidationResult> qui inclut la nouvelle <xref:System.Printing.PrintTicket> comme l’un de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="e1c9a-126">L’exemple vérifie ensuite que la nouvelle <xref:System.Printing.PrintTicket> recto verso des demandes.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="e1c9a-127">Dans ce cas, l’exemple met à nouveau ticket d’impression par défaut pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="e1c9a-128">Si l’étape 2 ci-dessus avait été ignorée et l’imprimante ne prenait pas en charge recto verso le long du côté long, puis aurait pour résultat le test `false`.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="e1c9a-129">(Voir la Remarque ci-dessus.)</span><span class="sxs-lookup"><span data-stu-id="e1c9a-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="e1c9a-130">La dernière étape importante consiste à valider la modification à la <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriété de la <xref:System.Printing.PrintQueue> avec la <xref:System.Printing.PrintQueue.Commit%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e1c9a-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="e1c9a-131">Afin que vous pouvez rapidement tester cet exemple, le reste est présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="e1c9a-132">Créez un projet et un espace de noms, puis collez les deux extraits de code dans cet article dans le bloc d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e1c9a-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="e1c9a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c9a-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="e1c9a-134">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="e1c9a-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="e1c9a-135">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="e1c9a-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="e1c9a-136">Schéma d’impression</span><span class="sxs-lookup"><span data-stu-id="e1c9a-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)
