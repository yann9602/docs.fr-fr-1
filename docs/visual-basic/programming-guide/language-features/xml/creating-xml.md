---
title: "Création de code XML dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95ab82f2a8ae11b04e3887d5a179931c47346155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="dc1ff-102">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc1ff-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dc1ff-103">Vous pouvez ainsi utiliser *littéraux XML* directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="dc1ff-104">La syntaxe de littéral XML représente [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets et il est similaire à la syntaxe XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="dc1ff-105">Cela rend plus facile de créer par programmation des éléments, des documents et des fragments XML, car votre code possède la même structure que le XML final.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc1ff-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dc1ff-106">In This Section</span></span>  
  
|<span data-ttu-id="dc1ff-107">Terme</span><span class="sxs-lookup"><span data-stu-id="dc1ff-107">Term</span></span>|<span data-ttu-id="dc1ff-108">Définition</span><span class="sxs-lookup"><span data-stu-id="dc1ff-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="dc1ff-109">Vue d’ensemble des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="dc1ff-110">Introduction aux littéraux XML et comment elles se rapportent à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc1ff-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="dc1ff-111">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="dc1ff-112">Décrit comment utiliser des expressions incorporées dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="dc1ff-113">Guide pratique : créer des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="dc1ff-114">Décrit comment créer un élément XML dans le code à l’aide d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="dc1ff-115">Espaces blancs dans les littéraux XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="dc1ff-116">Décrit comment [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] traite l’espace blanc dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-116">Describes how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="dc1ff-117">Littéraux XML et spécification XML 1.0</span><span class="sxs-lookup"><span data-stu-id="dc1ff-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="dc1ff-118">Décrit comment la syntaxe de littéral XML dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] se rapporte à la spécification XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="dc1ff-119">Guide pratique : incorporer des expressions dans des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="dc1ff-120">Décrit comment utiliser des expressions incorporées dans les littéraux XML pour créer le contenu au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="dc1ff-121">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="dc1ff-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="dc1ff-122">Décrit les conventions de dénomination des éléments et attributs XML.</span><span class="sxs-lookup"><span data-stu-id="dc1ff-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc1ff-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc1ff-123">See Also</span></span>  
 [<span data-ttu-id="dc1ff-124">XML</span><span class="sxs-lookup"><span data-stu-id="dc1ff-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
