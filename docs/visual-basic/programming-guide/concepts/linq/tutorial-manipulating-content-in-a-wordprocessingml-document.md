---
title: "Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f8028ba8-2dd1-4425-930c-8cc23176ebbc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 28ab2d19cba0344868061fbe1f59c546a569fbdc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-visual-basic"></a><span data-ttu-id="5faaf-102">Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-102">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>
<span data-ttu-id="5faaf-103">Ce didacticiel montre comment appliquer l'approche transformationnelle fonctionnelle et LINQ to XML pour manipuler des documents XML.</span><span class="sxs-lookup"><span data-stu-id="5faaf-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="5faaf-104">Les exemples Visual Basic interrogent et manipulent des informations dans des documents WordprocessingML Office Open XML enregistrés par Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="5faaf-104">The Visual Basic examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="5faaf-105">Pour plus d’informations, consultez la [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) site Web.</span><span class="sxs-lookup"><span data-stu-id="5faaf-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5faaf-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5faaf-106">In This Section</span></span>  
  
|<span data-ttu-id="5faaf-107">Rubrique</span><span class="sxs-lookup"><span data-stu-id="5faaf-107">Topic</span></span>|<span data-ttu-id="5faaf-108">Description</span><span class="sxs-lookup"><span data-stu-id="5faaf-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5faaf-109">Forme des Documents WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-109">Shape of WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="5faaf-110">Fournit une explication rapide des détails d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="5faaf-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="5faaf-111">Création du Document Office Open XML Source (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-111">Creating the Source Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="5faaf-112">Fournit des instructions détaillées pour créer le document source pour les requêtes dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="5faaf-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="5faaf-113">Recherche du Style de paragraphe par défaut (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-113">Finding the Default Paragraph Style (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="5faaf-114">Illustre une requête pour rechercher le nom du style par défaut pour un document.</span><span class="sxs-lookup"><span data-stu-id="5faaf-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="5faaf-115">Récupération des paragraphes et leurs Styles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-115">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="5faaf-116">Illustre une requête qui récupère une collection des paragraphes d’un document.</span><span class="sxs-lookup"><span data-stu-id="5faaf-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="5faaf-117">Récupération du texte des paragraphes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-117">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="5faaf-118">Étend la requête précédente pour récupérer le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="5faaf-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="5faaf-119">Refactorisation à l’aide d’une méthode d’Extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-119">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="5faaf-120">Simplifie le code par refactorisation à l’aide d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="5faaf-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="5faaf-121">Refactorisation à l’aide d’une fonction Pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-121">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="5faaf-122">Simplifie davantage le code par refactorisation à l'aide d'une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="5faaf-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="5faaf-123">Projection de code XML en une autre forme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-123">Projecting XML in a Different Shape (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="5faaf-124">Effectue une transformation XML en projetant du code XML d'une forme autre que celle du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="5faaf-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="5faaf-125">Rechercher du texte dans des Documents Word (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-125">Finding Text in Word Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="5faaf-126">Utilise les requêtes précédentes pour rechercher une chaîne de texte spécifiée dans un document.</span><span class="sxs-lookup"><span data-stu-id="5faaf-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="5faaf-127">Détails d’Office Open XML WordprocessingML Documents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faaf-127">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="5faaf-128">Fournit des détails relatifs aux documents WordprocessingML Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="5faaf-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5faaf-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5faaf-129">See Also</span></span>  
 <span data-ttu-id="5faaf-130">[Transformations fonctionnelles pures de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="5faaf-130">[Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
<span data-ttu-id="5faaf-131"> [Introduction aux Transformations fonctionnelles pures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="5faaf-131"> [Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span></span>
