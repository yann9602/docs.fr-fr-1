---
title: "Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)"
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
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 293e8de848f83517211e3f3ed640102a2c534764
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="0b369-102">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="0b369-103">Ce didacticiel montre comment appliquer l'approche transformationnelle fonctionnelle et LINQ to XML pour manipuler des documents XML.</span><span class="sxs-lookup"><span data-stu-id="0b369-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="0b369-104">Les exemples C# interrogent et manipulent des informations dans des documents WordprocessingML Office Open XML enregistrés par Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="0b369-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="0b369-105">Pour plus d’informations, consultez le site web [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573).</span><span class="sxs-lookup"><span data-stu-id="0b369-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b369-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0b369-106">In This Section</span></span>  
  
|<span data-ttu-id="0b369-107">Rubrique</span><span class="sxs-lookup"><span data-stu-id="0b369-107">Topic</span></span>|<span data-ttu-id="0b369-108">Description</span><span class="sxs-lookup"><span data-stu-id="0b369-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0b369-109">Forme des documents WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="0b369-110">Fournit une explication rapide des détails d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="0b369-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="0b369-111">Création du document Office Open XML source (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="0b369-112">Fournit des instructions détaillées pour créer le document source pour les requêtes dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="0b369-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="0b369-113">Recherche du style de paragraphe par défaut (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="0b369-114">Illustre une requête pour rechercher le nom du style par défaut pour un document.</span><span class="sxs-lookup"><span data-stu-id="0b369-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="0b369-115">Récupération des paragraphes et de leurs styles (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="0b369-116">Illustre une requête qui récupère une collection des paragraphes d’un document.</span><span class="sxs-lookup"><span data-stu-id="0b369-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="0b369-117">Récupération du texte des paragraphes (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="0b369-118">Étend la requête précédente pour récupérer le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="0b369-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="0b369-119">Refactorisation à l’aide d’une méthode d’extension (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="0b369-120">Simplifie le code par refactorisation à l’aide d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="0b369-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="0b369-121">Refactorisation à l’aide d’une fonction pure (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="0b369-122">Simplifie davantage le code par refactorisation à l'aide d'une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="0b369-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="0b369-123">Projection de code XML en une autre forme (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="0b369-124">Effectue une transformation XML en projetant du code XML d'une forme autre que celle du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="0b369-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="0b369-125">Recherche de texte dans des documents Word (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="0b369-126">Utilise les requêtes précédentes pour rechercher une chaîne de texte spécifiée dans un document.</span><span class="sxs-lookup"><span data-stu-id="0b369-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="0b369-127">Détails des documents WordprocessingML Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="0b369-128">Fournit des détails relatifs aux documents WordprocessingML Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="0b369-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b369-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b369-129">See Also</span></span>  
 <span data-ttu-id="0b369-130">[Transformations fonctionnelles pures de données XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0b369-130">[Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
 [<span data-ttu-id="0b369-131">Introduction aux transformations fonctionnelles pures (C#)</span><span class="sxs-lookup"><span data-stu-id="0b369-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)

