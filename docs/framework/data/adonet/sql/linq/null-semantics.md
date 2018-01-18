---
title: "Sémantique Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a><span data-ttu-id="fbd4c-102">Sémantique Null</span><span class="sxs-lookup"><span data-stu-id="fbd4c-102">Null Semantics</span></span>
<span data-ttu-id="fbd4c-103">Le tableau suivant fournit des liens vers différentes parties de la documentation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] où les problèmes relatifs à `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) sont abordés.</span><span class="sxs-lookup"><span data-stu-id="fbd4c-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="fbd4c-104">Rubrique</span><span class="sxs-lookup"><span data-stu-id="fbd4c-104">Topic</span></span>|<span data-ttu-id="fbd4c-105">Description</span><span class="sxs-lookup"><span data-stu-id="fbd4c-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fbd4c-106">Incompatibilité entre types SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="fbd4c-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="fbd4c-107">La section « Sémantique Null » de cette rubrique inclut une présentation des expressions booléennes SQL à trois valeurs par rapport aux valeurs <xref:System.Boolean>Common Language Runtime (CLR), `Nothing` littéral ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) et `null` (C#) ainsi que d'autres problèmes semblables.</span><span class="sxs-lookup"><span data-stu-id="fbd4c-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="fbd4c-108">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="fbd4c-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="fbd4c-109">La section « Sémantique Null » de cette rubrique décrit la sémantique de comparaison Null dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbd4c-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="fbd4c-110">System.String, méthodes</span><span class="sxs-lookup"><span data-stu-id="fbd4c-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="fbd4c-111">La section « Différences par rapport à .NET » de cette rubrique décrit comment un retour de 0 de <xref:System.String.LastIndexOf%2A> peut signifier que la chaîne a la valeur null ou que la position trouvée est 0.</span><span class="sxs-lookup"><span data-stu-id="fbd4c-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="fbd4c-112">Calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="fbd4c-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="fbd4c-113">Décrit comment l'opérateur <xref:System.Linq.Enumerable.Sum%2A> prend la valeur `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) au lieu de 0 pour une séquence qui contient uniquement des valeurs null ou pour une séquence vide.</span><span class="sxs-lookup"><span data-stu-id="fbd4c-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbd4c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbd4c-114">See Also</span></span>  
 [<span data-ttu-id="fbd4c-115">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="fbd4c-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
