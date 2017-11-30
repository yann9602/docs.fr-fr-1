---
title: "Opérateur GetXmlNamespace (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="f7324-102">Opérateur GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7324-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="f7324-103">Obtient le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7324-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7324-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7324-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="f7324-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f7324-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="f7324-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f7324-106">Optional.</span></span> <span data-ttu-id="f7324-107">Chaîne qui identifie le préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="f7324-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="f7324-108">Si spécifié, cette chaîne doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="f7324-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="f7324-109">Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f7324-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="f7324-110">Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné.</span><span class="sxs-lookup"><span data-stu-id="f7324-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="f7324-111">Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retournée.</span><span class="sxs-lookup"><span data-stu-id="f7324-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7324-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7324-112">Return Value</span></span>  
 <span data-ttu-id="f7324-113">Le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="f7324-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7324-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="f7324-114">Remarks</span></span>  
 <span data-ttu-id="f7324-115">Le `GetXmlNamespace` opérateur Obtient le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="f7324-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="f7324-116">Vous pouvez utiliser les préfixes d’espace de noms XML directement dans les littéraux XML et les propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="f7324-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="f7324-117">Toutefois, vous devez utiliser le `GetXmlNamespace` pour convertir un préfixe d’espace de noms pour un <xref:System.Xml.Linq.XNamespace> de l’objet avant de pouvoir l’utiliser dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f7324-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="f7324-118">Vous pouvez ajouter un nom d’élément non qualifié à un <xref:System.Xml.Linq.XNamespace> objet à obtenir un complet <xref:System.Xml.Linq.XName> de l’objet, que de nombreuses [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] méthodes requièrent.</span><span class="sxs-lookup"><span data-stu-id="f7324-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7324-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="f7324-119">Example</span></span>  
 <span data-ttu-id="f7324-120">L’exemple suivant importe `ns` comme un préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="f7324-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f7324-121">Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant qui a le nom qualifié `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="f7324-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="f7324-122">Il passe ensuite ce nœud enfant à la `ShowName` sous-routine qui construit un nom qualifié à l’aide de la `GetXmlNamespace` opérateur.</span><span class="sxs-lookup"><span data-stu-id="f7324-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="f7324-123">Le `ShowName` sous-routine transmet ensuite le nom qualifié à la <xref:System.Xml.Linq.XNode.Ancestors%2A> méthode pour obtenir le parent `ns:contact` nœud.</span><span class="sxs-lookup"><span data-stu-id="f7324-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="f7324-124">Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, il affiche un message qui contient le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f7324-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="f7324-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7324-125">See Also</span></span>  
 [<span data-ttu-id="f7324-126">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="f7324-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="f7324-127">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7324-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
