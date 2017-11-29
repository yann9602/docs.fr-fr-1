---
title: "Création d'un DataReader"
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05b3943613a6ab03e77dee7fb8262029618b5c7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datareader"></a><span data-ttu-id="1b347-102">Création d'un DataReader</span><span class="sxs-lookup"><span data-stu-id="1b347-102">Creating a DataReader</span></span>
<span data-ttu-id="1b347-103">Les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet> ont une méthode <xref:System.Data.DataTable.CreateDataReader%2A> qui retourne le contenu de la collection <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> ou de l'objet <xref:System.Data.DataSet.Tables%2A> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="1b347-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b347-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b347-104">Example</span></span>  
 <span data-ttu-id="1b347-105">L'application console suivante crée une instance de l'objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1b347-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="1b347-106">L’exemple passe ensuite la pleine <xref:System.Data.DataTable> à une procédure qui appelle la <xref:System.Data.DataTable.CreateDataReader%2A> méthode qui effectue une itération dans les résultats contenus dans le <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="1b347-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="1b347-107">L'exemple affiche la sortie suivante dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="1b347-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b347-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b347-108">See Also</span></span>  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [<span data-ttu-id="1b347-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="1b347-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="1b347-110">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="1b347-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
