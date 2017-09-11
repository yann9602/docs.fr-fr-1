---
title: "Émission d'assemblys et de méthodes dynamiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c28a5b71a93ea5159adc73316771d490dbe0db87
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="70a76-102">Émission d'assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="70a76-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="70a76-103">Cette section décrit un ensemble de types managés dans l'espace de noms <xref:System.Reflection.Emit>, qui permettent à un compilateur ou à un outil d'émettre des métadonnées et du langage MSIL (Microsoft Intermediate Language) au moment de l'exécution et de générer éventuellement un fichier exécutable portable sur le disque.</span><span class="sxs-lookup"><span data-stu-id="70a76-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="70a76-104">Les moteurs de script et les compilateurs sont les principaux utilisateurs de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="70a76-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="70a76-105">Dans cette section, la fonctionnalité fournies par l'espace de noms <xref:System.Reflection.Emit> est appelée émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="70a76-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="70a76-106">L'émission de réflexion offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="70a76-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="70a76-107">Définir des méthodes globales légères au moment de l'exécution à l'aide de la classe <xref:System.Reflection.Emit.DynamicMethod>, et les exécuter à l'aide de délégués.</span><span class="sxs-lookup"><span data-stu-id="70a76-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="70a76-108">Définir des assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="70a76-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="70a76-109">Définir des assemblys au moment de l'exécution, les exécuter, puis les décharger et autoriser le garbage collection à libérer leurs ressources.</span><span class="sxs-lookup"><span data-stu-id="70a76-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="70a76-110">Définir des modules dans de nouveaux assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="70a76-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="70a76-111">Définir des types dans des modules au moment de l'exécution, créer des instances de ces types et appeler leurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="70a76-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="70a76-112">Définir des informations symboliques pour des modules définis, qui peut être utilisées par des outils comme des débogueurs et des profileurs de code.</span><span class="sxs-lookup"><span data-stu-id="70a76-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="70a76-113">En plus des types managés dans l’espace de noms <xref:System.Reflection.Emit>, il existe des interfaces de métadonnées non managées qui sont décrites dans la documentation de référence [Interfaces de métadonnées](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="70a76-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="70a76-114">L'émission de réflexion managée offre une vérification des erreurs sémantiques plus puissante et un niveau d'abstraction des métadonnées plus élevé que les interfaces de métadonnées non managées.</span><span class="sxs-lookup"><span data-stu-id="70a76-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="70a76-115">Une autre ressource utile pour travailler avec les métadonnées et MSIL est la documentation de la Common Language Infrastructure (CLI), en particulier "Partie II : définition et sémantique des métadonnées" et "Partie III : jeu d'instructions de CIL".</span><span class="sxs-lookup"><span data-stu-id="70a76-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="70a76-116">La documentation est disponible en ligne sur [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) et sur le [site web Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="70a76-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70a76-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="70a76-117">In This Section</span></span>  
 [<span data-ttu-id="70a76-118">Problèmes de sécurité dans l’émission de réflexion</span><span class="sxs-lookup"><span data-stu-id="70a76-118">Security Issues in Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 <span data-ttu-id="70a76-119">Décrit les problèmes de sécurité liés à la création d'assemblys dynamiques en utilisant l'émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="70a76-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70a76-120">Référence</span><span class="sxs-lookup"><span data-stu-id="70a76-120">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="70a76-121">Répertorie les codes des instructions MSIL que vous pouvez utiliser pour créer des corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="70a76-121">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="70a76-122">Contient des classes managées utilisées pour émettre des méthodes, des assemblys et des types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="70a76-122">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="70a76-123">Décrit la classe <xref:System.Type>, qui représente des types dans la réflexion managée et dans l'émission de réflexion, et qui est essentielle dans l'utilisation de ces technologies.</span><span class="sxs-lookup"><span data-stu-id="70a76-123">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="70a76-124">Contient des classes managées utilisées pour explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="70a76-124">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70a76-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="70a76-125">Related Sections</span></span>  
 [<span data-ttu-id="70a76-126">Réflexion</span><span class="sxs-lookup"><span data-stu-id="70a76-126">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="70a76-127">Explique comment explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="70a76-127">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="70a76-128">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="70a76-128">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="70a76-129">Donne une vue d'ensemble des assemblys dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70a76-129">Provides an overview of assemblies in the .NET Framework.</span></span>

