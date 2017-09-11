---
title: "Transformations fonctionnelles pures de données XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ee60c400bb9bff719f818ab5a5a0a3c667a1b412
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="b7e0b-102">Transformations fonctionnelles pures de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7e0b-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="b7e0b-103">Cette section fournit un didacticiel sur les transformations fonctionnelles de données XML.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="b7e0b-104">Elle contient des explications des principaux concepts et constructions que vous devez comprendre pour utiliser des transformations fonctionnelles, ainsi que des exemples d'utilisation de transformations fonctionnelles pour manipuler un document XML.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="b7e0b-105">Bien que ce didacticiel contienne des exemples de code LINQ to XML, tous les concepts sous-jacents s'appliquent également à d'autres technologies LINQ.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="b7e0b-106">Le didacticiel [Manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) fournit une série d’exemples, chacun basé sur le précédent.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="b7e0b-107">Ces exemples illustrent l'approche transformationnelle fonctionnelle pure de la manipulation de données XML.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="b7e0b-108">Ce didacticiel suppose que vous connaissez le langage C#.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="b7e0b-109">Aucune sémantique détaillée des constructions propres au langage n'est fournie dans ce didacticiel, mais des liens sont fournis vers la documentation de langage appropriée.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="b7e0b-110">On suppose également que vous avez une connaissance pratique des concepts informatiques de base et du langage XML, y compris les espaces de noms XML.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7e0b-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b7e0b-111">In This Section</span></span>  
  
|<span data-ttu-id="b7e0b-112">Rubrique</span><span class="sxs-lookup"><span data-stu-id="b7e0b-112">Topic</span></span>|<span data-ttu-id="b7e0b-113">Description</span><span class="sxs-lookup"><span data-stu-id="b7e0b-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b7e0b-114">Introduction aux transformations fonctionnelles pures (C#)</span><span class="sxs-lookup"><span data-stu-id="b7e0b-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="b7e0b-115">Décrit les transformations fonctionnelles et définit la terminologie appropriée.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="b7e0b-116">Didacticiel : Chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="b7e0b-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="b7e0b-117">Décrit l'évaluation et l'exécution différées en détail.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="b7e0b-118">Didacticiel : Manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7e0b-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="b7e0b-119">Didacticiel qui illustre une transformation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="b7e0b-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7e0b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e0b-120">See Also</span></span>  
 [<span data-ttu-id="b7e0b-121">Interrogation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7e0b-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

