---
title: "Datasets typés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a68d4a10b01285a7e1b33238409351ca04d0aeb4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="typed-datasets"></a><span data-ttu-id="2411f-102">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="2411f-102">Typed DataSets</span></span>
<span data-ttu-id="2411f-103">En plus d'un accès par liaison tardive aux valeurs via des variables faiblement typées, l'objet <xref:System.Data.DataSet> permet un accès aux données par l'intermédiaire d'une métaphore fortement typée.</span><span class="sxs-lookup"><span data-stu-id="2411f-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="2411f-104">Tables et colonnes qui font partie de la **DataSet** accessibles à l’aide de noms conviviaux et de variables fortement typées.</span><span class="sxs-lookup"><span data-stu-id="2411f-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="2411f-105">Typé **DataSet** est une classe qui dérive d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2411f-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="2411f-106">Par conséquent, il hérite de toutes les méthodes, événements et propriétés d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2411f-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="2411f-107">En outre, un typé **DataSet** fournit des méthodes fortement typées, propriétés et événements.</span><span class="sxs-lookup"><span data-stu-id="2411f-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="2411f-108">Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d’utiliser les méthodes associées à des collections.</span><span class="sxs-lookup"><span data-stu-id="2411f-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="2411f-109">À l’exception d’améliorer la lisibilité du code, un typé **DataSet** autorise également le code de Visual Studio .NET éditeur compléter automatiquement les lignes en cours de frappe.</span><span class="sxs-lookup"><span data-stu-id="2411f-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="2411f-110">En outre, fortement typé **DataSet** donne accès aux valeurs avec le type approprié au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2411f-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="2411f-111">Avec fortement typé **DataSet**, erreurs d’incompatibilité de type sont interceptées lorsque le code est compilé et non au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2411f-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2411f-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2411f-112">In This Section</span></span>  
 [<span data-ttu-id="2411f-113">Génération de DataSets fortement typés</span><span class="sxs-lookup"><span data-stu-id="2411f-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="2411f-114">Décrit comment créer et utiliser fortement typé **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2411f-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="2411f-115">Annotation de DataSets typés</span><span class="sxs-lookup"><span data-stu-id="2411f-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="2411f-116">Explique comment annoter le schéma XML Schema definition language (XSD) utilisé pour générer un fortement typée **DataSet**afin de donner aux **DataSet** noms conviviaux d’éléments sans pour autant modifier le schéma sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="2411f-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2411f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2411f-117">See Also</span></span>  
 [<span data-ttu-id="2411f-118">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="2411f-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="2411f-119">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="2411f-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
