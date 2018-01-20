---
title: "Modélisation et mappage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0782d75aa44557ef87f1d59757b0d60873d8a949
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="db138-102">Modélisation et mappage</span><span class="sxs-lookup"><span data-stu-id="db138-102">Modeling and Mapping</span></span>
<span data-ttu-id="db138-103">Dans [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez définir le modèle conceptuel, le modèle de stockage et le mappage entre les deux de la façon la plus appropriée pour votre application.</span><span class="sxs-lookup"><span data-stu-id="db138-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="db138-104">Les outils Entity Data Model dans [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] vous permettent de créer un.[ fichier edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) à partir d’une base de données ou un modèle graphique et puis mettez à jour ce fichier lorsque la base de données ou le modèle change.</span><span class="sxs-lookup"><span data-stu-id="db138-104">The Entity Data Model Tools in [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] allow you to create an .[edmx file](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="db138-105">Depuis Entity Framework 4.1, vous pouvez également créer un modèle par programme à l’aide du développement Code First.</span><span class="sxs-lookup"><span data-stu-id="db138-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="db138-106">Il existe deux scénarios différents pour le développement Code First.</span><span class="sxs-lookup"><span data-stu-id="db138-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="db138-107">Dans les deux cas, le développeur définit un modèle lors du codage des définitions de classe .NET Framework, puis spécifie éventuellement un mappage supplémentaire ou une configuration supplémentaire à l'aide des annotations de données ou de l'API Fluent.</span><span class="sxs-lookup"><span data-stu-id="db138-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="db138-108">Pour plus d’informations, consultez [création et mappage d’un modèle conceptuel](http://go.microsoft.com/fwlink/?LinkId=235016).</span><span class="sxs-lookup"><span data-stu-id="db138-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="db138-109">Vous pouvez également utiliser l’outil EDM Generator, qui est inclus dans le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db138-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="db138-110">EdmGen.exe génère les fichiers .csdl, .ssdl et .msl d'une source de données existante.</span><span class="sxs-lookup"><span data-stu-id="db138-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="db138-111">Vous pouvez également créer manuellement le modèle et mapper le contenu.</span><span class="sxs-lookup"><span data-stu-id="db138-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="db138-112">Pour plus d’informations, consultez [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="db138-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
