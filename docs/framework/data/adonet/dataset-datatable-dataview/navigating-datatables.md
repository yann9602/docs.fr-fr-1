---
title: Navigation sur les DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: de3d0125adc6f18ebebf13ff3cf2fa5119ec17df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datatables"></a><span data-ttu-id="4086b-102">Navigation sur les DataTable</span><span class="sxs-lookup"><span data-stu-id="4086b-102">Navigating DataTables</span></span>
<span data-ttu-id="4086b-103">L'objet <xref:System.Data.DataTableReader> obtient le contenu d'un ou plusieurs objets <xref:System.Data.DataTable> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="4086b-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="4086b-104">Un objet <xref:System.Data.DataTableReader> peut contenir plusieurs jeux de résultats s'il est créé à l'aide de la méthode <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="4086b-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="4086b-105">S'il y a plusieurs jeux de résultats, la méthode <xref:System.Data.DataTableReader.NextResult%2A> déplace le curseur sur le jeu de résultats suivant.</span><span class="sxs-lookup"><span data-stu-id="4086b-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="4086b-106">Il s'agit d'un processus en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="4086b-106">This is a forward-only process.</span></span> <span data-ttu-id="4086b-107">Il n'est pas possible de revenir à un jeu de résultats précédent.</span><span class="sxs-lookup"><span data-stu-id="4086b-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4086b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4086b-108">Example</span></span>  
 <span data-ttu-id="4086b-109">Dans l’exemple suivant, la `TestConstructor` méthode crée deux <xref:System.Data.DataTable> instances.</span><span class="sxs-lookup"><span data-stu-id="4086b-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="4086b-110">Pour montrer ce constructeur pour le <xref:System.Data.DataTableReader> (classe), l’exemple crée un **DataTableReader** basé sur un tableau qui contient les deux **DataTables**et effectue une opération simple, impression du contenu à partir des premières colonnes dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4086b-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4086b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4086b-111">See Also</span></span>  
 [<span data-ttu-id="4086b-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="4086b-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="4086b-113">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="4086b-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
