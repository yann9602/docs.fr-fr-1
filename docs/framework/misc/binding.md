---
title: '&lt;liaison&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eefa3145f50ffa24c1b3cf895c9e5097adb5e9d9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindinggt"></a><span data-ttu-id="a2310-102">&lt;liaison&gt;</span><span class="sxs-lookup"><span data-stu-id="a2310-102">&lt;binding&gt;</span></span>
<span data-ttu-id="a2310-103">Vous pouvez utiliser l'élément de `binding` pour configurer différents types de liaisons prédéfinies fournis par Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a2310-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="a2310-104">Liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="a2310-104">System-Provided Binding</span></span>  
 <span data-ttu-id="a2310-105">Les liaisons fournies par le système masquent la complexité de la pile de la messagerie du WCF.</span><span class="sxs-lookup"><span data-stu-id="a2310-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a2310-106">Les applications qui utilisent des liaisons fournies par le système ne requièrent pas de contrôle total sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a2310-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a2310-107">Les attributs exposés sur chaque liaison fournie par le système sont les plus appropriés pour le scénario d'utilisation des adresses de liaison.</span><span class="sxs-lookup"><span data-stu-id="a2310-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="a2310-108">La section de configuration de chaque liaison fournie par le système peut définir plusieurs configurations utilisées en vue de configurer la liaison.</span><span class="sxs-lookup"><span data-stu-id="a2310-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a2310-109">Chaque configuration est identifiée par un nom unique.</span><span class="sxs-lookup"><span data-stu-id="a2310-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="a2310-110">Il n'est pas possible d'ajouter des éléments ou des attributs à une liaison fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="a2310-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a2310-111">Pour cela, vous devez implémenter une liaison personnalisée, telle que décrite dans la section « Liaison personnalisée » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a2310-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="a2310-112">Il est possible de définir une liaison personnalisée qui imite parfaitement une liaison fournie par le système et ajoute quelques paramètres sur lesquels l'utilisateur de l'application souhaite avoir le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a2310-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="a2310-113">Liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="a2310-113">Custom Binding</span></span>  
 <span data-ttu-id="a2310-114">Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.</span><span class="sxs-lookup"><span data-stu-id="a2310-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a2310-115">Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.</span><span class="sxs-lookup"><span data-stu-id="a2310-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a2310-116">Chaque élément définit et configure l'élément de la pile.</span><span class="sxs-lookup"><span data-stu-id="a2310-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a2310-117">Il doit y avoir un seul élément de `transport` dans chaque liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a2310-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a2310-118">Sans cet élément, la pile de messagerie est incomplète.</span><span class="sxs-lookup"><span data-stu-id="a2310-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a2310-119">L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.</span><span class="sxs-lookup"><span data-stu-id="a2310-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a2310-120">Voici l'ordre recommandé des éléments de la pile :</span><span class="sxs-lookup"><span data-stu-id="a2310-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a2310-121">Transactions (facultatif)</span><span class="sxs-lookup"><span data-stu-id="a2310-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a2310-122">Messagerie fiable (facultatif)</span><span class="sxs-lookup"><span data-stu-id="a2310-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a2310-123">Sécurité (facultatif)</span><span class="sxs-lookup"><span data-stu-id="a2310-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a2310-124">Encodeur</span><span class="sxs-lookup"><span data-stu-id="a2310-124">Encoder</span></span>  
  
5.  <span data-ttu-id="a2310-125">Transport</span><span class="sxs-lookup"><span data-stu-id="a2310-125">Transport</span></span>  
  
 <span data-ttu-id="a2310-126">Les liaisons personnalisées sont identifiées par leur attribut `name`.</span><span class="sxs-lookup"><span data-stu-id="a2310-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2310-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2310-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="a2310-128">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a2310-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a2310-129">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a2310-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a2310-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a2310-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
