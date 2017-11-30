---
title: Transformations XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="9c0f1-102">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="9c0f1-102">XSLT Transformations</span></span>
<span data-ttu-id="9c0f1-103">Les transformations XSLT (Extensible Stylesheet Language Transformation) ont pour but de transformer le contenu d'un document XML source en un autre document dont le format ou la structure diffère.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="9c0f1-104">Par exemple, vous pouvez utiliser XSLT pour transformer un document XML en un document HTML pour une utilisation sur un site web ou en un document qui contient uniquement les champs requis par une application.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="9c0f1-105">Ce processus de transformation est spécifié par le [recommandation W3C XSL Transformations (XSLT) Version 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="9c0f1-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="9c0f1-106">La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="9c0f1-107">La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge la recommandation du W3C sur XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c0f1-108">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="9c0f1-109">La classe <xref:System.Xml.Xsl.XslCompiledTransform> est une nouvelle implémentation du moteur XSLT.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="9c0f1-110">Elle inclut des améliorations de performances et de nouvelles fonctions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="9c0f1-111">La pratique recommandée consiste à créer des applications XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c0f1-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9c0f1-112">In This Section</span></span>  
 [<span data-ttu-id="9c0f1-113">À l’aide de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9c0f1-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="9c0f1-114">Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="9c0f1-115">Migration à partir de la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="9c0f1-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="9c0f1-116">Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="9c0f1-117">Compilateur XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="9c0f1-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="9c0f1-118">Fournit des informations sur l'utilisation de XSLT Compiler.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="9c0f1-119">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="9c0f1-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="9c0f1-120">Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="9c0f1-121">**Remarque** la <xref:System.Xml.Xsl.XslTransform> classe est obsolète dans la .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c0f1-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9c0f1-122">Référence</span><span class="sxs-lookup"><span data-stu-id="9c0f1-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="9c0f1-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9c0f1-123">Related Sections</span></span>  
 [<span data-ttu-id="9c0f1-124">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="9c0f1-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
