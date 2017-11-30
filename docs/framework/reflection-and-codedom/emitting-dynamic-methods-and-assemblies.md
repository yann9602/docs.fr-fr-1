---
title: "Émission d'assemblys et de méthodes dynamiques"
ms.custom: 
ms.date: 08/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91b0cc4614834f2ad8f7b54d9364d484ca9a6990
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="adf65-102">Émission d'assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="adf65-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="adf65-103">Cette section décrit un ensemble de types managés dans l'espace de noms <xref:System.Reflection.Emit>, qui permettent à un compilateur ou à un outil d'émettre des métadonnées et du langage MSIL (Microsoft Intermediate Language) au moment de l'exécution et de générer éventuellement un fichier exécutable portable sur le disque.</span><span class="sxs-lookup"><span data-stu-id="adf65-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="adf65-104">Les moteurs de script et les compilateurs sont les principaux utilisateurs de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="adf65-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="adf65-105">Dans cette section, la fonctionnalité fournies par l'espace de noms <xref:System.Reflection.Emit> est appelée émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="adf65-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="adf65-106">L'émission de réflexion offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="adf65-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="adf65-107">Définir des méthodes globales légères au moment de l'exécution à l'aide de la classe <xref:System.Reflection.Emit.DynamicMethod>, et les exécuter à l'aide de délégués.</span><span class="sxs-lookup"><span data-stu-id="adf65-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="adf65-108">Définir des assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="adf65-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="adf65-109">Définir des assemblys au moment de l'exécution, les exécuter, puis les décharger et autoriser le garbage collection à libérer leurs ressources.</span><span class="sxs-lookup"><span data-stu-id="adf65-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="adf65-110">Définir des modules dans de nouveaux assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="adf65-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="adf65-111">Définir des types dans des modules au moment de l'exécution, créer des instances de ces types et appeler leurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="adf65-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="adf65-112">Définir des informations symboliques pour des modules définis, qui peut être utilisées par des outils comme des débogueurs et des profileurs de code.</span><span class="sxs-lookup"><span data-stu-id="adf65-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="adf65-113">En plus des types managés dans l’espace de noms <xref:System.Reflection.Emit>, il existe des interfaces de métadonnées non managées qui sont décrites dans la documentation de référence [Interfaces de métadonnées](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="adf65-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="adf65-114">L'émission de réflexion managée offre une vérification des erreurs sémantiques plus puissante et un niveau d'abstraction des métadonnées plus élevé que les interfaces de métadonnées non managées.</span><span class="sxs-lookup"><span data-stu-id="adf65-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="adf65-115">Une autre ressource utile pour travailler avec les métadonnées et MSIL est la documentation de la Common Language Infrastructure (CLI), en particulier "Partie II : définition et sémantique des métadonnées" et "Partie III : jeu d'instructions de CIL".</span><span class="sxs-lookup"><span data-stu-id="adf65-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="adf65-116">La documentation est disponible en ligne sur [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) et sur le [site web Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="adf65-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adf65-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="adf65-117">In This Section</span></span>
  
[<span data-ttu-id="adf65-118">Émettre des problèmes de sécurité dans la réflexion</span><span class="sxs-lookup"><span data-stu-id="adf65-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="adf65-119">Décrit les problèmes de sécurité liés à la création d'assemblys dynamiques en utilisant l'émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="adf65-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="adf65-120">[Comment : définir et exécuter des méthodes dynamiques](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="adf65-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="adf65-121">Montre comment exécuter une méthode dynamique simple et une méthode dynamique est lié à une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="adf65-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="adf65-122">[Comment : définir un type générique avec la réflexion émettre](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="adf65-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="adf65-123">Montre comment créer un type générique simple avec deux paramètres de type, comment appliquer une classe, interface et les contraintes spéciales aux paramètres de type et comment créer memers qui utilisent des paramètres de type de la classe comme types de paramètres et types de retour.</span><span class="sxs-lookup"><span data-stu-id="adf65-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create memers that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="adf65-124">[Comment : définir une méthode générique avec la réflexion émettre](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="adf65-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="adf65-125">Montre comment créer, émettre et appeler une méthode générique simple.</span><span class="sxs-lookup"><span data-stu-id="adf65-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="adf65-126">[Assemblys pouvant être collectés pour la génération de type dynamique](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="adf65-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="adf65-127">Introduit les assemblys pouvant être collectés, qui sont des assemblys dynamiques qui peuvent être déchargés sans décharger le domaine d’application dans lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="adf65-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="adf65-128">Référence</span><span class="sxs-lookup"><span data-stu-id="adf65-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="adf65-129">Répertorie les codes des instructions MSIL que vous pouvez utiliser pour créer des corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="adf65-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="adf65-130">Contient des classes managées utilisées pour émettre des méthodes, des assemblys et des types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="adf65-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="adf65-131">Décrit la classe <xref:System.Type>, qui représente des types dans la réflexion managée et dans l'émission de réflexion, et qui est essentielle dans l'utilisation de ces technologies.</span><span class="sxs-lookup"><span data-stu-id="adf65-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="adf65-132">Contient des classes managées utilisées pour explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="adf65-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="adf65-133">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="adf65-133">Related Sections</span></span>  
 [<span data-ttu-id="adf65-134">Réflexion</span><span class="sxs-lookup"><span data-stu-id="adf65-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="adf65-135">Explique comment explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="adf65-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="adf65-136">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="adf65-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="adf65-137">Fournit une vue d’ensemble des assemblys dans les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="adf65-137">Provides an overview of assemblies in .NET implementations.</span></span>
