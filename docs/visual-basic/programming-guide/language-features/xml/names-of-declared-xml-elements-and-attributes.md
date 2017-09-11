---
title: "Noms des éléments XML déclarés et attributs (Visual Basic) | Documents Microsoft"
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
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2c0bb2350f50138d00e202e2e887a2202d21942f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="86f9d-102">Nom des attributs et des éléments XML déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86f9d-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="86f9d-103">Cette rubrique fournit des [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] conseils pour les noms des éléments XML et des attributs dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="86f9d-103">This topic provides [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="86f9d-104">Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié.</span><span class="sxs-lookup"><span data-stu-id="86f9d-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="86f9d-105">Un nom qualifié se compose d’un préfixe d’espace de noms XML, un signe deux-points et un nom local.</span><span class="sxs-lookup"><span data-stu-id="86f9d-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="86f9d-106">Pour plus d’informations sur les préfixes d’espace de noms XML, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="86f9d-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="86f9d-107">Règles</span><span class="sxs-lookup"><span data-stu-id="86f9d-107">Rules</span></span>  
 <span data-ttu-id="86f9d-108">Un nom local d’un élément ou attribut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doivent respecter les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="86f9d-108">A local name of an element or attribute in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="86f9d-109">Il peut commencer par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="86f9d-109">It can begin with a namespace.</span></span> <span data-ttu-id="86f9d-110">Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="86f9d-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="86f9d-111">Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, points (.) et des traits d’union (-).</span><span class="sxs-lookup"><span data-stu-id="86f9d-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="86f9d-112">Il ne doit pas être supérieure à 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="86f9d-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="86f9d-113">Les deux-points qui figurent dans les noms indiquent la délimitation d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="86f9d-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="86f9d-114">Par conséquent, vous pouvez utiliser les deux-points uniquement pour spécifier un espace de noms XML pour un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="86f9d-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="86f9d-115">En outre, vous devez respecter la règle suivante.</span><span class="sxs-lookup"><span data-stu-id="86f9d-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="86f9d-116">La spécification XML 1.0 préserve tous les noms commençant par la chaîne « xml » de toute variation de mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="86f9d-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="86f9d-117">Par conséquent, n’utilisez pas ces noms pour l’élément et les noms d’attributs.</span><span class="sxs-lookup"><span data-stu-id="86f9d-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="86f9d-118">Instructions de longueur de nom</span><span class="sxs-lookup"><span data-stu-id="86f9d-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="86f9d-119">Dans la pratique, un nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément.</span><span class="sxs-lookup"><span data-stu-id="86f9d-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="86f9d-120">Cela améliore la lisibilité de votre code et réduit la taille de fichier source et de longueur de ligne.</span><span class="sxs-lookup"><span data-stu-id="86f9d-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="86f9d-121">Toutefois, votre nom ne doit pas être court qu’il ne pas décrire suffisamment l’élément ou la façon dont votre code utilise.</span><span class="sxs-lookup"><span data-stu-id="86f9d-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="86f9d-122">Ceci est important pour la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="86f9d-122">This is important for the readability of your code.</span></span> <span data-ttu-id="86f9d-123">Si une autre personne essaie de le comprendre ou si vous devez l’observer longtemps après que l’avoir écrit, ce nom peut gagner du temps.</span><span class="sxs-lookup"><span data-stu-id="86f9d-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="86f9d-124">Respect de la casse dans les noms</span><span class="sxs-lookup"><span data-stu-id="86f9d-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="86f9d-125">Noms d’éléments XML respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="86f9d-125">XML element names are case sensitive.</span></span> <span data-ttu-id="86f9d-126">Cela signifie que lorsque la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur compare deux noms qui ne diffèrent que par la casse, il les interprète comme deux noms différents.</span><span class="sxs-lookup"><span data-stu-id="86f9d-126">This means that when the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="86f9d-127">Par exemple, il interprète `ABC` et `abc` comme deux éléments distincts.</span><span class="sxs-lookup"><span data-stu-id="86f9d-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="86f9d-128">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="86f9d-128">XML Namespaces</span></span>  
 <span data-ttu-id="86f9d-129">Lorsque vous créez un élément XML littérale, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="86f9d-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="86f9d-130">Pour plus d’informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="86f9d-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f9d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f9d-131">See Also</span></span>  
 <span data-ttu-id="86f9d-132">[Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="86f9d-132">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="86f9d-133"> [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span><span class="sxs-lookup"><span data-stu-id="86f9d-133"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span></span>
