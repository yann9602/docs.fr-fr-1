---
title: "Nom des attributs et des éléments XML déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="17b4e-102">Nom des attributs et des éléments XML déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17b4e-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="17b4e-103">Cette rubrique fournit des [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] conseils pour les noms des éléments XML et les attributs dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="17b4e-103">This topic provides [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="17b4e-104">Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié.</span><span class="sxs-lookup"><span data-stu-id="17b4e-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="17b4e-105">Un nom qualifié se compose d’un préfixe d’espace de noms XML, un signe deux-points et un nom local.</span><span class="sxs-lookup"><span data-stu-id="17b4e-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="17b4e-106">Pour plus d’informations sur les préfixes d’espace de noms XML, consultez [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="17b4e-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="17b4e-107">Règles</span><span class="sxs-lookup"><span data-stu-id="17b4e-107">Rules</span></span>  
 <span data-ttu-id="17b4e-108">Un nom local d’un élément ou attribut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doivent respecter les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="17b4e-108">A local name of an element or attribute in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="17b4e-109">Il peut commencer par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="17b4e-109">It can begin with a namespace.</span></span> <span data-ttu-id="17b4e-110">Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="17b4e-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="17b4e-111">Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, des points (.) et des traits d’union (-).</span><span class="sxs-lookup"><span data-stu-id="17b4e-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="17b4e-112">Il ne doit pas être supérieure à 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="17b4e-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="17b4e-113">Les deux-points qui figurent dans les noms indiquent la délimitation d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="17b4e-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="17b4e-114">Par conséquent, vous pouvez utiliser des signes deux-points uniquement pour spécifier un espace de noms XML pour un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="17b4e-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="17b4e-115">En outre, vous devez respecter la règle suivante.</span><span class="sxs-lookup"><span data-stu-id="17b4e-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="17b4e-116">La spécification XML 1.0 réserve tous les noms commençant par la chaîne « xml » de toute variation de la mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="17b4e-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="17b4e-117">Par conséquent, n’utilisez pas ces noms pour votre élément et les noms d’attributs.</span><span class="sxs-lookup"><span data-stu-id="17b4e-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="17b4e-118">Instructions de longueur de nom</span><span class="sxs-lookup"><span data-stu-id="17b4e-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="17b4e-119">Dans la pratique, un nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément.</span><span class="sxs-lookup"><span data-stu-id="17b4e-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="17b4e-120">Cela améliore la lisibilité de votre code et réduit la taille du fichier source et de longueur de ligne.</span><span class="sxs-lookup"><span data-stu-id="17b4e-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="17b4e-121">Toutefois, votre nom ne doit pas être court qu’il ne pas décrive correctement l’élément ou la façon dont votre code utilise.</span><span class="sxs-lookup"><span data-stu-id="17b4e-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="17b4e-122">Ceci est important pour la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="17b4e-122">This is important for the readability of your code.</span></span> <span data-ttu-id="17b4e-123">Si quelqu'un d’autre tente de le comprendre, ou si vous devez l’observer longtemps après que l’avoir écrit, noms d’éléments appropriés peuvent gagner du temps.</span><span class="sxs-lookup"><span data-stu-id="17b4e-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="17b4e-124">Respect de la casse dans les noms</span><span class="sxs-lookup"><span data-stu-id="17b4e-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="17b4e-125">Noms d’éléments XML respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="17b4e-125">XML element names are case sensitive.</span></span> <span data-ttu-id="17b4e-126">Cela signifie que lorsque la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur compare deux noms qui ne diffèrent que par la casse, il les interprète comme deux noms différents.</span><span class="sxs-lookup"><span data-stu-id="17b4e-126">This means that when the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="17b4e-127">Par exemple, il interprète `ABC` et `abc` comme deux éléments distincts.</span><span class="sxs-lookup"><span data-stu-id="17b4e-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="17b4e-128">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="17b4e-128">XML Namespaces</span></span>  
 <span data-ttu-id="17b4e-129">Lorsque vous créez un élément XML littéral, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="17b4e-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="17b4e-130">Pour plus d’informations, consultez [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="17b4e-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b4e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17b4e-131">See Also</span></span>  
 [<span data-ttu-id="17b4e-132">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17b4e-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="17b4e-133">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="17b4e-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
