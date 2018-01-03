---
title: '&lt;liaisons&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d89fc465c1e82fab638b57dbf712f1396385f80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="75792-102">&lt;liaisons&gt;</span><span class="sxs-lookup"><span data-stu-id="75792-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="75792-103">Cette section contient une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="75792-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="75792-104">Chaque entrée est un élément de `binding` qui peut être identifié par son `name` unique.</span><span class="sxs-lookup"><span data-stu-id="75792-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="75792-105">Les services utilisent les liaisons en les liant à l'aide de `name`.</span><span class="sxs-lookup"><span data-stu-id="75792-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="75792-106">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="75792-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="75792-107">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="75792-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="75792-108">Liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="75792-108">System-Provided Binding</span></span>  
 <span data-ttu-id="75792-109">Les liaisons fournies par le système masquent la complexité de la pile de la messagerie du WCF.</span><span class="sxs-lookup"><span data-stu-id="75792-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="75792-110">Les applications qui utilisent des liaisons fournies par le système ne requièrent pas de contrôle total sur la pile.</span><span class="sxs-lookup"><span data-stu-id="75792-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="75792-111">Les attributs exposés sur chaque liaison fournie par le système sont les plus appropriés pour le scénario d'utilisation des adresses de liaison.</span><span class="sxs-lookup"><span data-stu-id="75792-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="75792-112">La section de configuration de chaque liaison fournie par le système peut définir plusieurs configurations utilisées en vue de configurer la liaison.</span><span class="sxs-lookup"><span data-stu-id="75792-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="75792-113">Chaque configuration est identifiée par un nom unique.</span><span class="sxs-lookup"><span data-stu-id="75792-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="75792-114">Il n'est pas possible d'ajouter des éléments ou des attributs à une liaison fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="75792-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="75792-115">Pour cela, vous devez implémenter une liaison personnalisée, telle que décrite dans la section « Liaison personnalisée » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="75792-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="75792-116">Il est possible de définir une liaison personnalisée qui imite parfaitement une liaison fournie par le système et ajoute quelques paramètres sur lesquels l’utilisateur de l’application souhaite avoir le contrôle.</span><span class="sxs-lookup"><span data-stu-id="75792-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="75792-117">Pour obtenir la liste des liaisons fournies par le système, consultez [les liaisons fournies](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="75792-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="75792-118">Liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="75792-118">Custom Binding</span></span>  
 <span data-ttu-id="75792-119">Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.</span><span class="sxs-lookup"><span data-stu-id="75792-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="75792-120">Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.</span><span class="sxs-lookup"><span data-stu-id="75792-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="75792-121">Chaque élément définit et configure l'élément de la pile.</span><span class="sxs-lookup"><span data-stu-id="75792-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="75792-122">Il doit y avoir un seul élément de `transport` dans chaque liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="75792-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="75792-123">Sans cet élément, la pile de messagerie est incomplète.</span><span class="sxs-lookup"><span data-stu-id="75792-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="75792-124">L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.</span><span class="sxs-lookup"><span data-stu-id="75792-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="75792-125">Voici l'ordre requis des éléments de la pile :</span><span class="sxs-lookup"><span data-stu-id="75792-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="75792-126">Transactions (facultatif)</span><span class="sxs-lookup"><span data-stu-id="75792-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="75792-127">Messagerie fiable (facultatif)</span><span class="sxs-lookup"><span data-stu-id="75792-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="75792-128">Sécurité (facultatif)</span><span class="sxs-lookup"><span data-stu-id="75792-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="75792-129">Encodeur</span><span class="sxs-lookup"><span data-stu-id="75792-129">Encoder</span></span>  
  
5.  <span data-ttu-id="75792-130">Transport</span><span class="sxs-lookup"><span data-stu-id="75792-130">Transport</span></span>  
  
 <span data-ttu-id="75792-131">Les liaisons personnalisées sont identifiées par leur attribut `name`.</span><span class="sxs-lookup"><span data-stu-id="75792-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="75792-132">Pour plus d’informations sur les liaisons personnalisées, consultez [des liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="75792-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75792-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75792-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="75792-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="75792-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="75792-135">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="75792-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="75792-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="75792-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="75792-137">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="75792-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
