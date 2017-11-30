---
title: "Objets d’extension XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2916f7da6b990cddef9b86559a71b5206351d558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="c453e-102">Objets d’extension XSLT</span><span class="sxs-lookup"><span data-stu-id="c453e-102">XSLT Extension Objects</span></span>
<span data-ttu-id="c453e-103">Les objets d’extension permettent d’étendre les fonctionnalités des feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="c453e-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="c453e-104">Ils sont gérés par la classe <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="c453e-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="c453e-105">L'utilisation d'un objet d'extension plutôt que d'un script intégré présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="c453e-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="c453e-106">Offre une meilleure encapsulation et réutilisation des classes.</span><span class="sxs-lookup"><span data-stu-id="c453e-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="c453e-107">Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="c453e-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="c453e-108">Des objets d'extension XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c453e-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="c453e-109">Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.</span><span class="sxs-lookup"><span data-stu-id="c453e-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c453e-110">Le jeu d'autorisations FullTrust est requis pour appeler la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c453e-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="c453e-111">Pour plus d’informations, consultez [Code Access Security](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) et [NIB : jeux d’autorisations nommés](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="c453e-111">For more information, see [Code Access Security](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="c453e-112">Les types de données retournés par les objets d'extension correspondent à l'un des quatre types de données de base XPath : `number`, `string`, `Boolean` et `node set`.</span><span class="sxs-lookup"><span data-stu-id="c453e-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="c453e-113">Les méthodes définies avec le mot clé `params`, qui permet de transmettre un nombre non spécifié de paramètres, ne sont actuellement pas prises en charge par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c453e-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c453e-114">Les feuilles de style XSLT qui utilisent une méthode définie avec le mot clé `params` ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="c453e-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="c453e-115">Pour plus d’informations, consultez [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="c453e-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="c453e-116">Pour utiliser un objet d’extension XSLT</span><span class="sxs-lookup"><span data-stu-id="c453e-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="c453e-117">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l'objet d'extension à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c453e-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="c453e-118">Appelez l'objet d'extension à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="c453e-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="c453e-119">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="c453e-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c453e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c453e-120">See Also</span></span>  
 [<span data-ttu-id="c453e-121">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="c453e-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="c453e-122">Considérations sur la sécurité XSLT</span><span class="sxs-lookup"><span data-stu-id="c453e-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
