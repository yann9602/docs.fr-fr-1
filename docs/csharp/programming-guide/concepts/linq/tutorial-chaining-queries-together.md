---
title: "Didacticiel : chaînage de requêtes (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08196f4780e566cc05e36b6cfe78caad3e9c96a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="d8d0e-102">Didacticiel : chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="d8d0e-103">Ce didacticiel illustre le modèle de traitement lorsque vous chaînez des requêtes.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="d8d0e-104">Le chaînage de requêtes est un aspect essentiel de l'écriture des transformations fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="d8d0e-105">Il est important de comprendre exactement comment fonctionnent les requêtes chaînées.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="d8d0e-106">Les requêtes qui traitent des documents Office Open XML utilisent cette technique de manière intensive.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8d0e-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d8d0e-107">In This Section</span></span>  
  
|<span data-ttu-id="d8d0e-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="d8d0e-108">Topic</span></span>|<span data-ttu-id="d8d0e-109">Description</span><span class="sxs-lookup"><span data-stu-id="d8d0e-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d8d0e-110">Exécution et évaluation différées dans LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="d8d0e-111">Décrit les concepts d'évaluation et d'exécution différées.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="d8d0e-112">Exemple d’exécution différée (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="d8d0e-113">Fournit un exemple d'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="d8d0e-114">Exemple de chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="d8d0e-115">Montre comment fonctionne l'exécution différée lors du chaînage de requêtes.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="d8d0e-116">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="d8d0e-117">Identifie et illustre la sémantique de matérialisation intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="d8d0e-118">Chaînage d’opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="d8d0e-119">Décrit la sémantique différée des opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="d8d0e-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8d0e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8d0e-120">See Also</span></span>  
 [<span data-ttu-id="d8d0e-121">Transformations fonctionnelles pures de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d0e-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
