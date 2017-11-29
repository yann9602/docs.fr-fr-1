---
title: "Accès au code XML dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="dab12-102">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dab12-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dab12-103">Fournit des propriétés d’axe XML pour accéder à et naviguer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span><span class="sxs-lookup"><span data-stu-id="dab12-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="dab12-104">Ces propriétés utilisent une syntaxe spéciale pour vous permettre d’accéder aux éléments et attributs en spécifiant les noms XML.</span><span class="sxs-lookup"><span data-stu-id="dab12-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="dab12-105">Le tableau suivant répertorie les fonctionnalités de langage qui vous permettent d’accéder aux éléments et attributs dans XML [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dab12-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="dab12-106">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="dab12-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="dab12-107">Description de la propriété</span><span class="sxs-lookup"><span data-stu-id="dab12-107">Property description</span></span>|<span data-ttu-id="dab12-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="dab12-108">Example</span></span>|<span data-ttu-id="dab12-109">Description</span><span class="sxs-lookup"><span data-stu-id="dab12-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="dab12-110">*axe d’enfant*</span><span class="sxs-lookup"><span data-stu-id="dab12-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="dab12-111">Obtient tous les `phone` les éléments qui sont des éléments enfants de le `contact` élément.</span><span class="sxs-lookup"><span data-stu-id="dab12-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="dab12-112">*axe d’attribut*</span><span class="sxs-lookup"><span data-stu-id="dab12-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="dab12-113">Obtient tous les `type` les attributs de la `phone` élément.</span><span class="sxs-lookup"><span data-stu-id="dab12-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="dab12-114">*axe descendant*</span><span class="sxs-lookup"><span data-stu-id="dab12-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="dab12-115">Obtient tous les `name` les éléments de la `contacts` élément, quelle que soit la profondeur dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="dab12-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="dab12-116">*indexeur d’extension*</span><span class="sxs-lookup"><span data-stu-id="dab12-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="dab12-117">Obtient le premier `name` élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="dab12-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="dab12-118">*value*</span><span class="sxs-lookup"><span data-stu-id="dab12-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="dab12-119">Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.</span><span class="sxs-lookup"><span data-stu-id="dab12-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="dab12-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dab12-120">In This Section</span></span>  
 [<span data-ttu-id="dab12-121">Guide pratique : accéder à des éléments descendants XML</span><span class="sxs-lookup"><span data-stu-id="dab12-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="dab12-122">Montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML qui ont un nom spécifié et qui sont contenus sous un élément XML spécifié.</span><span class="sxs-lookup"><span data-stu-id="dab12-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="dab12-123">Guide pratique : accéder à des éléments enfants XML</span><span class="sxs-lookup"><span data-stu-id="dab12-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="dab12-124">Montre comment utiliser un enfant de propriété d’axe pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="dab12-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="dab12-125">Guide pratique : accéder à des attributs XML</span><span class="sxs-lookup"><span data-stu-id="dab12-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="dab12-126">Montre comment utiliser la propriété d’axe d’attribut pour accéder à tous les attributs XML qui ont un nom spécifié dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="dab12-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="dab12-127">Guide pratique : déclarer et utiliser des préfixes d’espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="dab12-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="dab12-128">Montre comment déclarer un préfixe d’espace de noms XML et l’utiliser pour créer et accéder à des éléments XML.</span><span class="sxs-lookup"><span data-stu-id="dab12-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dab12-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="dab12-129">Related Sections</span></span>  
 [<span data-ttu-id="dab12-130">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="dab12-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="dab12-131">Fournit des liens vers des sections qui décrivent les différentes propriétés d’accès XML.</span><span class="sxs-lookup"><span data-stu-id="dab12-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="dab12-132">Vue d’ensemble de LINQ to XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dab12-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="dab12-133">Fournit une introduction à l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dab12-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="dab12-134">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dab12-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="dab12-135">Fournit une introduction à l’aide de littéraux XML en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dab12-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="dab12-136">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dab12-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="dab12-137">Fournit des liens vers les sections sur le chargement et la modification de XML en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dab12-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="dab12-138">XML</span><span class="sxs-lookup"><span data-stu-id="dab12-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="dab12-139">Fournit des liens vers des sections qui décrivent comment utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dab12-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
