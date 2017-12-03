---
title: "Comment : personnaliser une liaison fournie par le système"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c46886879d19d612827b94821e0105c68c437c56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="46696-102">Comment : personnaliser une liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="46696-102">How to: Customize a System-Provided Binding</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="46696-103"> inclut plusieurs liaisons fournies par le système qui vous permettent de configurer quelques-unes des propriétés des éléments de liaison sous-jacents, mais pas toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="46696-103"> includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="46696-104">Cette rubrique explique comment attribuer des propriétés aux éléments de liaison afin de créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="46696-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="46696-105">comment créer directement et configurer des éléments de liaison sans utiliser les liaisons fournies par le système, consultez [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="46696-105"> how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="46696-106">Création et l’extension de liaisons personnalisées, consultez [extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="46696-106"> creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="46696-107">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] toutes les liaisons sont composées de *éléments de liaison*.</span><span class="sxs-lookup"><span data-stu-id="46696-107">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="46696-108">Chaque élément de liaison dérive de la classe <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="46696-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="46696-109">Les liaisons fournies par le système telles que <xref:System.ServiceModel.BasicHttpBinding> créent et configurent leurs propres éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="46696-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="46696-110">Cette rubrique vous indique comment accéder aux propriétés de ces éléments de liaison qui ne sont pas exposés directement sur la liaison et comment les modifier ; il s'agit, notamment, de la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="46696-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="46696-111">Les éléments de liaison individuels sont inclus dans une collection représentée par la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et sont ajoutés dans l'ordre suivant : Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding et Transport.</span><span class="sxs-lookup"><span data-stu-id="46696-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="46696-112">Notez que les éléments de liaison répertoriés ne sont pas tous requis dans chaque liaison.</span><span class="sxs-lookup"><span data-stu-id="46696-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="46696-113">Les éléments de liaison définis par l'utilisateur peuvent également apparaître dans cette collection et doivent figurer dans le même ordre que précédemment.</span><span class="sxs-lookup"><span data-stu-id="46696-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="46696-114">Par exemple, un transport défini par l'utilisateur doit être le dernier élément de la collection d'éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="46696-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="46696-115">La classe <xref:System.ServiceModel.BasicHttpBinding> contient trois éléments de liaison :</span><span class="sxs-lookup"><span data-stu-id="46696-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1.  <span data-ttu-id="46696-116">Un élément de liaison de sécurité facultatif, soit la classe <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> utilisée avec le transport HTTP (sécurité de niveau transport), soit la classe <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> utilisée lorsque la couche transport fournit la sécurité, auquel cas le transport HTTPS est utilisé.</span><span class="sxs-lookup"><span data-stu-id="46696-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2.  <span data-ttu-id="46696-117">Un élément de liaison d'encodeur de message requis, <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ou <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="46696-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3.  <span data-ttu-id="46696-118">Un élément de liaison de transport requis, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="46696-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="46696-119">Dans cet exemple, nous allons créer une instance de la liaison, générer un *liaison personnalisée* à partir de celui-ci, examinez les éléments de liaison dans la liaison personnalisée, et lorsque nous aurons trouvé l’élément de liaison HTTP, nous avons défini son `KeepAliveEnabled` propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="46696-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="46696-120">La propriété `KeepAliveEnabled` n'est pas exposée directement sur `BasicHttpBinding`, nous devons donc créer une liaison personnalisée pour naviguer jusqu'à l'élément de liaison et définir cette propriété.</span><span class="sxs-lookup"><span data-stu-id="46696-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="46696-121">Pour modifier une liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="46696-121">To modify a system-provided binding</span></span>  
  
1.  <span data-ttu-id="46696-122">Créez une instance de la classe <xref:System.ServiceModel.BasicHttpBinding> et affectez à son mode de sécurité la valeur de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="46696-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  <span data-ttu-id="46696-123">Créez une liaison personnalisée à partir de la liaison et ensuite une classe <xref:System.ServiceModel.Channels.BindingElementCollection> à partir de l'une des propriétés de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="46696-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <span data-ttu-id="46696-124">Parcourez la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et lorsque vous trouverez la classe <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, affectez à sa propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="46696-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="46696-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46696-125">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="46696-126">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="46696-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
