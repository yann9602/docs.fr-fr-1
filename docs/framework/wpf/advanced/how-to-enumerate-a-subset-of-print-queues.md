---
title: "Comment : énumérer un sous-ensemble de files d'attente à l'impression"
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
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 397ec40e2d8a0694e208296593687e9268546fc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="472f5-102">Comment : énumérer un sous-ensemble de files d'attente à l'impression</span><span class="sxs-lookup"><span data-stu-id="472f5-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="472f5-103">Une situation courante rencontrée par les professionnels informatiques (IT) de la gestion d’un ensemble d’échelle de la société d’imprimantes est pour générer une liste des imprimantes présentant certaines caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="472f5-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="472f5-104">Cette fonctionnalité est fournie par le <xref:System.Printing.PrintServer.GetPrintQueues%2A> méthode d’un <xref:System.Printing.PrintServer> objet et le <xref:System.Printing.EnumeratedPrintQueueTypes> énumération.</span><span class="sxs-lookup"><span data-stu-id="472f5-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="472f5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="472f5-105">Example</span></span>  
 <span data-ttu-id="472f5-106">Dans l’exemple ci-dessous, le code commence par créer un tableau d’indicateurs qui spécifient les caractéristiques des files d’attente, que nous souhaitons liste.</span><span class="sxs-lookup"><span data-stu-id="472f5-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="472f5-107">Dans cet exemple, nous recherchons les files d’attente qui sont installées localement sur le serveur d’impression et sont partagés.</span><span class="sxs-lookup"><span data-stu-id="472f5-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="472f5-108">Le <xref:System.Printing.EnumeratedPrintQueueTypes> énumération offre de nombreuses autres possibilités.</span><span class="sxs-lookup"><span data-stu-id="472f5-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="472f5-109">Le code crée ensuite un <xref:System.Printing.LocalPrintServer> de l’objet, une classe dérivée de <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="472f5-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="472f5-110">Le serveur d’impression local est l’ordinateur sur lequel l’application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="472f5-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="472f5-111">La dernière étape importante consiste à passer le tableau à la <xref:System.Printing.PrintServer.GetPrintQueues%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="472f5-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="472f5-112">Enfin, les résultats sont présentés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="472f5-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="472f5-113">Vous pouvez étendre cet exemple en ayant la `foreach` boucle parcourt chaque file d’attente d’impression faire davantage de filtrage.</span><span class="sxs-lookup"><span data-stu-id="472f5-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="472f5-114">Par exemple, vous pourriez filtrer les imprimantes qui ne gèrent pas l’impression recto-verso en demandant à l’appel de la boucle chaque file d’attente à l’impression <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> (méthode) et test, la valeur retournée pour la présence de duplex.</span><span class="sxs-lookup"><span data-stu-id="472f5-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="472f5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="472f5-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="472f5-116">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="472f5-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="472f5-117">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="472f5-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="472f5-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="472f5-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
