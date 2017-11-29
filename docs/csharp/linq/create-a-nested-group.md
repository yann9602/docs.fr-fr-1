---
title: "Créer un groupe imbriqué"
description: "Indique comment créer un groupe imbriqué."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="3cec5-104">Créer un groupe imbriqué</span><span class="sxs-lookup"><span data-stu-id="3cec5-104">Create a nested group</span></span>

<span data-ttu-id="3cec5-105">L’exemple suivant montre comment créer des groupes imbriqués dans une expression de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="3cec5-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="3cec5-106">Chaque groupe créé en fonction de l’année/du niveau d’étude est ensuite encore subdivisé en groupes en fonction des noms des individus.</span><span class="sxs-lookup"><span data-stu-id="3cec5-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cec5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cec5-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="3cec5-108">Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="3cec5-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="3cec5-109">Notez que trois boucles `foreach` imbriquées sont nécessaires pour effectuer une itération sur les éléments internes d’un groupe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="3cec5-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cec5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cec5-110">See also</span></span>  
 [<span data-ttu-id="3cec5-111">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="3cec5-111">LINQ Query Expressions</span></span>](index.md)
