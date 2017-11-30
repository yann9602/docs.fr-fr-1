---
title: Fonctions spatiales
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a><span data-ttu-id="cbee6-102">Fonctions spatiales</span><span class="sxs-lookup"><span data-stu-id="cbee6-102">Spatial Functions</span></span>
<span data-ttu-id="cbee6-103">Il n'existe aucun format littéral pour les types spatiaux.</span><span class="sxs-lookup"><span data-stu-id="cbee6-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="cbee6-104">Toutefois, vous pouvez utiliser des fonctions canoniques Entity Framework que vous appelez à l'aide de chaînes au format texte connu.</span><span class="sxs-lookup"><span data-stu-id="cbee6-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="cbee6-105">Par exemple, l'appel de fonction suivant crée un point géométrique :</span><span class="sxs-lookup"><span data-stu-id="cbee6-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="cbee6-106">Le [spatialedmfunctions, méthodes](http://msdn.microsoft.com/library/hh749531.aspx) page répertorie toutes les méthodes canoniques spatiales Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cbee6-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="cbee6-107">Cliquez sur une méthode qui vous intéresse pour afficher les paramètres qui doivent être passés à une fonction.</span><span class="sxs-lookup"><span data-stu-id="cbee6-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
